<template>
  <footer class="footer pb-5">
    <div class="content has-text-centered">
      <div v-if="disclaimer" class="footpad footer-disclaimer">
        <span class="disclaimer-head">Disclaimer:</span> &nbsp; Our resources are only for learning and communication, not for any commercial use. Please abide by the laws and regulations of your country, and any illegal behavior shall be borne by the user himself.
      </div>
      <div v-if="footerLogo" class="footpad footimage">
        <img width="150" height="75" class="gloryimage" :src="footerLogoLink">
      </div>
      <div class="footpad footicons">
         <font color='red'>3flix</font> | 2020 
      </div>
      <div v-if="copyright" class="footpad footer-copyright">
        Copyright&nbsp;<i class="fas fa-copyright"></i> {{ Date.now() | moment("YYYY") }} | &nbsp;{{ sitename }}
      </div>
      <div v-if="license" class="footpad footer-policy">
        Licensed under FrontEnd - <a href="https://github.com/rafsanbasunia/gindex-v4/LICENSE" target="_blank"> GPL 3.0 </a> | Backend - <a href="https://github.com/rafsanbasunia/gindex-v4/vuejs/LICENSE" target="_blank">MIT</a>
      </div>
      <div v-if="codeofconduct" class="footpad footer-code">
        Please Read our <a href="https://github.com/rafsanbasunia/gindex-v4/Terms_and_Conditions.md" target="_blank">Terms_and_Conditions</a> | <a href="https://github.com/rafsanbasunia/gindex-v4/CONTRIBUTING.md" target="_blank">Community Guidelines</a>
      </div>
    </div>
  </footer>
</template>
<script>
export default {
  props: {},
  data: function () {
    return {
      content: "",
      sitename: "",
      disclaimer: "",
      copyright: "",
      license: "",
      codeofconduct: "",
      footerLogo: false,
      footerLogoLink: "",
    };
  },
  components: {},
  methods: {},
  beforeMount(){
    this.sitename = document.getElementsByTagName("title")[0].innerText;
  },
  mounted() {
    this.$ga.page({
      page: this.$route.path,
      title: "Foot",
      location: window.location.href
    });
    this.$ga.event({eventCategory: "Site Initialized",eventAction: "Normal - "+this.siteName,eventLabel: "Foot",nonInteraction: true})
    this.copyright = window.themeOptions.footer_data.copyright;
    this.disclaimer = window.themeOptions.footer_data.disclaimer;
    this.license = window.themeOptions.footer_data.license;
    this.codeofconduct = window.themeOptions.footer_data.license;
    this.footerLogo = window.themeOptions.footer_data.footer_logo
    if(this.footerLogo){
      this.footerLogoLink = window.themeOptions.footer_data.footer_logo_link;
    } else {
      this.footerLogoLink = "";
    }
  },
  watch: {
    "$route": function() {
      this.$ga.event({eventCategory: "Route Change",eventAction: "Normal - "+this.siteName,eventLabel: "Foot",nonInteraction: true})
    }
  }
};
</script>
