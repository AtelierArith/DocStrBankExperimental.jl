バリアーアップインオプションの構造体

```
	barOption=BarrierOptionUpIn(T::num1,K::num2,barrier::num3,isCall::Bool=true) where {num1 <: Number,num2 <: Number,num3 <: Number}
```

ここで：

```
	T	    = オプションの満期までの時間。
	K	    = オプションの行使価格。
	barrier	= オプションの上バリア。
	isCall  = CALLの場合はtrue、PUTの場合はfalse。
```
