<template>
    <div class="container">
        <div
                v-for="post in posts"
                :key="post.data"
                class="card"
                style="width: 18rem;"
        >
            <h5 class="card-title"> {{ post.title }} </h5>
            <p class="card-text"> {{ post.body }} </p>
            <small class="card-user" v-for="user in users" :key="user.id"> {{ user.name }} </small>
        </div>
    </div>
</template>


<script>

    import axios from 'axios';

    export default {
        name: 'HelloWorld',
        data() {
            return {
                posts: [],
                users: [],
            };
        },
        mounted() {
            axios.get('http://jsonplaceholder.typicode.com/posts')
                .then(response => (this.posts = response.data))
                .catch(error => console.log(error));
            axios.get(' http://jsonplaceholder.typicode.com/users')
                .then(response => (this.users = response.data))
                .catch(error => console.log(error));
        }

    }


</script>


<style scoped>
    .container {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        align-items: flex-start;
    }

    .card {
        border: 1px solid lightblue;
        border-radius: 5px;
        margin: 15px;
        padding: 15px;
    }

    .card-title {
        color: cornflowerblue;
    }

    .card-user {
        color: #c9cdcf;
    }
</style>
