Struct for Asian Fixed Strike Option

```
	asOption=AsianFixedStrikeOption(T::num1,K::num2,isCall::Bool=true) where {num1 <: Number,num2 <: Number}
```

Where:

```
	T	    = Time to maturity of the Option.
	K	    = Strike Price of the Option.
	isCall  = true for CALL, false for PUT.
```
