欧州オプションの構造体

```
	euOption=EuropeanOption(T::num1,K::num2,isCall::Bool=true) where {num1 <: Number,num2 <: Number}
```

ここで：

```
	T	    = オプションの満期までの時間。
	K	    = オプションの行使価格。
isCall  = CALLの場合はtrue、PUTの場合はfalse。
```
