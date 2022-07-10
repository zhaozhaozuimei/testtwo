<template>
	<view class="container">
		<view class="header">
			<view class="city">
				<view class="content">
					平顶山
				</view>
				<view class="iconfont icon-down2 down">
				</view>
			</view>
			<view class="search">
				<view class="iconfont icon-fangdajing">
				</view>
				<view class="content">
					请输入商家名、品类或者商圈...
				</view>
			</view>
			<view class="personal">
				<image src="../../static/images/personal.png"></image>
			</view>
		</view>
		<view class="recommends">
			<view class="recList">
				<text class="iconfont icon-meishi">
				</text>
				<text class="content">
					美食
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon-maoyandianying">
				</text>
				<text class="content">
					猫眼电影
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon--jiudian">
				</text>
				<text class="content">
					酒店
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon-xx">
				</text>
				<text class="content">
					休闲娱乐
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon-waimai">
				</text>
				<text class="content">
					外卖
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon-ktv">
				</text>
				<text class="content">
					KTV
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon-zhoubianyou">
				</text>
				<text class="content">
					周边游
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon-liren">
				</text>
				<text class="content">
					丽人
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon-xiaochikuaican">
				</text>
				<text class="content">
					小吃快餐
				</text>
			</view>
			<view class="recList">
				<text class="iconfont icon-quanbufenlei">
				</text>
				<text class="content">
					全部分类
				</text>
			</view>
		</view>
		<view class="storeList">
			<view style="padding: 20rpx 0;">猜你喜欢</view>
			<view class="storeScroll">
				<view class="storeItem" v-for="(store,index) in storeList" :key='store.storeId'>
					<view class="img">
						<image :src="store.picUrl"></image>
					</view>
					<view class="storeDesc">
						<text>{{store.storeName}}</text>
						<view class="detail">{{store.description}}</view>
						<view class="price">
							<view class="desc">
								<text class="priceNumber">{{store.price[0]}}</text>
								<text style="color: #FF6639; font-size: 24rpx;	">元</text>
								<text style="color: #999999; font-size: 24rpx; 							margin-left: 4rpx;">
									门市价：{{store.price[1]}}元
								</text>
							</view>
							<view class="count1">
									<text class="count">已售{{store.count}}</text>
							</view>
						</view>
					</view>
					
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import request from '../../utils/request.js'
	export default {
		data() {
			return {
				storeList:[]
			}
		},
		onLoad() {
			this.getStoreLis()
		},
		methods: {
			//获取商家列表
			async getStoreLis(){
				this.storeList = await request('/getStoreList')
			}
		}
	}
</script>

<style lang="less">
	.container {
		background: #F0EFED;
		.header {
			display: flex;
			height: 101rpx;
			background: #FFCC00;

			.city {
				display: flex;
				width: 120rpx;
				height: 101rpx;
				line-height: 101rpx;
				text-align: center;
				margin-left: 40rpx;
				box-sizing: border-box;
				font-size: 28rpx;

				.iconfont {
					font-size: 20rpx;
					font-weight: 700;
					margin-left: 10rpx;
					color: #333333;
				}
			}

			.search {
				display: flex;
				width: 501rpx;
				height: 64rpx;
				background: #FFFFFF;
				border-radius: 20rpx;
				line-height: 64rpx;
				text-align: center;
				margin-top: 20rpx;
				padding-left: 25rpx;
				font-size: 28rpx;
				color: #C0C0C0;

				.content {
					margin-left: 18rpx;
				}
			}

			.personal {
				width: 94rpx;
				height: 101rpx;
				line-height: 101rpx;
				text-align: center;

				image {
					width: 48rpx;
					height: 48rpx;
					vertical-align: middle;
				}
			}
		}

		.recommends {
			background: white;
			display: -webkit-box;
			display: -webkit-flex;
			display: flex;
			-webkit-flex-wrap: wrap;
			flex-wrap: wrap;

			.recList {
				width: 150rpx;
				height: 140rpx;
				display: flex;
				flex-direction: column;
				padding: 20rpx 0;

				.iconfont {
					width: 80rpx;
					height: 80rpx;
					border-radius: 50%;
					background: #fd9d21;
					margin: 0 38rpx 10rpx;
					line-height: 80rpx;
					text-align: center;
					color: white;
				}

				.content {
					font-size: 24rpx;
					color: #666;
					margin: 0 auto;
				}
			}
		}
		.storeList{
			background: white;
			padding: 0 20rpx;
			margin-top: 20rpx;
			.storeScroll{
				.storeItem{
					width: 710rpx;
					display: flex;
					padding: 20rpx 0;
					border-top: 1rpx solid #808080;
					.img{
						width: 165rpx;
						height: 150rpx;
						margin-right: 20rpx;
						// display: inline-block;
						image{
							// display: block;
							width: 165rpx;
							height: 150rpx;
						}
					}
					.storeDesc{
						display: flex;
						flex-direction: column;
						//font-size: 30rpx;
						.detail{
							font-size: 24rpx;
							color: #808080;
							//max-width: 500rpx;
							overflow: hidden;
							text-overflow:ellipsis;
							white-space: nowrap;
						}
						.price{
							display: flex;
							//flex-direction: column;
							//justify-content: space-between;
							margin-top: 30rpx;;
							box-sizing: border-box;
							.desc{
								.priceNumber{
									font-size: 32rpx;
									color: #FF6639;
								}
							}
							.count1{
								//float: right;
								.count{
									font-size: 24rpx;
									color: #999999;
									margin-left: 160rpx;
								}
							}
						}
					}
				}
			}	
		}
	}
</style>
