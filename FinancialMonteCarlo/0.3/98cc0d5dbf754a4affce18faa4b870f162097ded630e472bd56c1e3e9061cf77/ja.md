アジア固定ストライクオプションの構造体

```
	asOption=AsianFixedStrikeOption(T::num1,K::num2,isCall::Bool=true) where {num1 <: Number,num2 <: Number}
```

ここで：

```
	T	    = オプションの満期までの時間。
	K	    = オプションのストライク価格。
	isCall  = CALLの場合はtrue、PUTの場合はfalse。
```
