<template>
    <div>
            <div class="alert alert-warning text-center" role="alert" v-show="!showAlert">
                <strong>Hey!</strong> {{alertMessage}}
            </div>
            <div class="displayContacts text-center">
                <p v-for="list in contacts">&#9702; {{list}} &nbsp; &nbsp; <button type="button" class="btn btn-outline-secondary btn-sm" v-on:click="deleteList">Delete</button></p>
            </div>
            <div class="row">
                <form class="col-md-3 contactForm" >
                    <div class="form-group">
                        <label for="name">Full Name</label>
                        <input type="text" class="form-control" id="name" placeholder="Enter Name" v-model="name">
                    </div>
                    <div class="form-group">
                        <label for="phone">Phone</label>
                        <input type="tel" class="form-control" id="phone" placeholder="Enter Phone number" v-model="phone">
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" class="form-control" id="email" placeholder="Enter Email" v-model="email">
                    </div>
                     <div class="text-center">
                        <button type="button" class="btn btn-outline-success btn-block" v-on:click.prevent="addContact">Add</button>
                    </div>
                </form>
            </div>
    </div>
</template>

<script>

    export default{

        data:function(){
            return{
                name:"",
                phone:"",
                email:"",
                contacts:[],
                showAlert:true,
                alertMessage:""
            }
        },

        methods:{

            addContact:function(){

                //check if the values are null.

                if(this.name != '' && this.phone != '' && this.email!= '') {
                    this.contacts.push("Name : " + this.name + " | Phone : " + this.phone + " | Email : " + this.email);

                    //reset the data in input boxes.

                    this.name ='';
                    this.phone ='';
                    this.email = '';
                    this.showAlert = true;
                } // if

                else if(this.name == '' || this.phone =='' || this.email ==''){

                    this.alertMessage = "Please fill the inputs."
                    this.showAlert = false;

                } // else if - three inputs are empty

            }, // addContact()

            deleteList:function(){

                this.contacts.pop();
            }

        }
    }
</script>

<style>
    .contactForm{
        margin: 3% auto;
    }
    .displayContacts{
        margin-top: 3%;
        margin-bottom: 5%;
        font-size: 21px;
        font-weight: 200;
    }
    .btn{
        cursor: pointer;
    }
</style>