<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Directives Exercise</h1>
                <p>Clicks count: <b>{{ clicksCount }}</b></p>
                <!-- Exercise -->
                <!-- Build a Custom Directive which works like v-on (Listen for Events) -->
                <button v-myListener="hasClicked">button</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
      data() {
        return {
          clicksCount: 0,
        }
      },
      methods: {
        hasClicked() {
          this.clicksCount++;
        }
      },
      directives: {
        myListener: {
          bind(el, binding, vnode) {
            el.onclick = function() {
              binding.value();
            }
            if(binding.arg == 'click') {

              // console.log(this.clicksCount);
              this.hasClicked();
            }
          }
        }
      }
    }
</script>

<style>
</style>
