<template lang="pug">
	aside.nav(:class="{ mini: minimized }")
		.menu
			.title {{ "General" | i18n }}
			ul
				router-link(tag="li", to="/")
					a(:title="_('Home')")
						span.icon
							i.fa.fa-home
						span.label {{ "Home" | i18n }}

				router-link(tag="li", to="/posts")
					a(:title="_('Posts')")
						span.icon
							i.fa.fa-comments
						span.label {{ "Posts" | i18n }}

				plaid-link(env="sandbox", publicKey="4e30ea23e5ed21daf34a766b0a22ca", clientName="Test App", product="transactions", v-bind="{ onSuccess }")
					span.label {{ "Accounts" | i18n }}

			.title {{ "Profile" | i18n }}
			ul
				li
					a(href="/logout", :title="_('Logout')")
						span.icon
							i.fa.fa-sign-out
						span.label {{ "Logout" | i18n }}

		.footer
			.social
				a(href="", target="_blank")
					i.fa.fa-facebook
				a(href="https://twitter.com/Icebobcsi", target="_blank")
					i.fa.fa-twitter
				a(href="https://github.com/icebob/vue-express-mongo-boilerplate", target="_blank")
					i.fa.fa-github
			.copyright &copy; Copyright, 2016
</template>

<script>
	import PlaidLink from 'vue-plaid-link';

	export default {
		components: {
			PlaidLink
		},
		props: [
			"minimized"
		],
		methods: {
			onSuccess (token, metadata) {
				console.log(token)
				console.log(metadata)
			}
		}
	};

</script>

<style lang="scss">
</style>
