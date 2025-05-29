ダブルバリアオプションの構造体

```
	dbOption=DoubleBarrierOption(T::num1,K::num2,D::num3,U::num4,isCall::Bool=true) where {num1 <: Number,num2 <: Number,num3 <: Number,num4 <: Number}
```

ここで：

```
	T	    = オプションの満期までの時間。
	K	    = オプションの行使価格。
	D	    = オプションの下限バリア。
	U	    = オプションの上限バリア。
	isCall  = CALLの場合はtrue、PUTの場合はfalse。
```
