Struct for Double Barrier Option

```
	dbOption=DoubleBarrierOption(T::num1,K::num2,D::num3,U::num4,isCall::Bool=true) where {num1 <: Number,num2 <: Number,num3 <: Number,num4 <: Number}
```

Where:

```
	T	    = Time to maturity of the Option.
	K	    = Strike Price of the Option.
	D	    = Low Barrier of the Option.
	U	    = Up Barrier of the Option.
	isCall  = true for CALL, false for PUT.
```
