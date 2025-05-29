Struct for Barrier Down and In Option

```
	barOption=BarrierOptionDownIn(T::num1,K::num2,barrier::num3,isCall::Bool=true) where {num1 <: Number,num2 <: Number,num3 <: Number}
```

Where:

```
	T	    = Time to maturity of the Option.
	K	    = Strike Price of the Option.
	barrier	= Down Barrier of the Option.
	isCall  = true for CALL, false for PUT.
```
