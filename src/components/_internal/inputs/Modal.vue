<!--
Input prompt based on this example:
https://codesandbox.io/s/github/vuejs/vuejs.org/tree/master/src/v2/examples/vue-20-modal-component
-->

<template>
	<transition name="modal">
		<div class="modal-mask">
			<div class="modal-wrapper">
				<div class="modal-container">
					<div class="modal-header">
						<slot name="header" />
					</div>

					<div class="modal-body">
						<slot name="body">
							Lorem ipsum dolor sit amet.
						</slot>
					</div>

					<div class="modal-footer">
						<slot name="footer" />
					</div>
				</div>
			</div>
		</div>
	</transition>
</template>

<script lang="ts">
import vue from "vue";

interface DataTypeDescriptor {

}

export default vue.extend({
	name: 'Modal',
	props: {
		visible: {
			type: Boolean,
			default: true,
		},
		title: {
			type: String,
			default: undefined,
		},
		description: {
			type: String,
			default: undefined,
		},
	},
	data() : DataTypeDescriptor {
		return { };
	},
})
</script>


<style scoped>
.modal-mask {
	position: fixed;
	z-index: 9998;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: rgba(0, 0, 0, 0.5);
	display: table;
	transition: opacity 0.3s ease;
}

.modal-wrapper {
	display: table-cell;
	vertical-align: middle;
}

.modal-container {
	display: flex;
	flex-direction: column;
	width: 400px;
	margin: 0 auto;
	padding: 20px 30px;
	background-color: #fff;
	border-radius: 2px;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
	transition: all 0.3s ease;
	font-family: Helvetica, Arial, sans-serif;
}

.modal-body {
	margin: 10px 0;
	flex: .8;
}

.modal-header, .modal-footer {

}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
	opacity: 0;
}

.modal-leave-active {
	opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
	-webkit-transform: scale(1.1);
	transform: scale(1.1);
}
</style>
