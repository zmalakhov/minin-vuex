<template>
    <div class="wrapper-content wrapper-content--fixed">
        <section>
            <div class="container">
                <PostForm></PostForm>
                <hr>
                <h1>{{ postsCount }}</h1>
                <div class="posts">
                    <div class="post" v-for="post in allPosts" :key="post.id">
                        <h2>{{ post.title }}</h2>
                        <p>{{ post.body }}</p>
                    </div>
                </div>


            </div>
        </section>
    </div>
</template>

<script>

    import {mapGetters, mapActions} from 'vuex'
    import PostForm from '../components/PostForm'

    export default {
        // computed:{
        //     allPosts(){
        //         return this.$store.getters.allPosts
        //     }
        // },
        computed: mapGetters(['allPosts','postsCount']),
        methods: mapActions(['fetchPosts']),
        components:{ PostForm },

        async mounted() {
            //this.$store.dispatch('fetchPosts')
            this.fetchPosts()
        }
    }
</script>

<style lang="scss">
    .posts {
        text-align: center;
        color: #2c3e50;
        margin: 60px auto;
        width: 400px;
        border: 1px solid violet;
    }

    .post {
        border: 1px solid #ccc;
        border-radius: 5px;
        margin-bottom: 1rem;
        h2 {
            font-weight: bold;
            margin: 1rem 0;
        }
    }
</style>