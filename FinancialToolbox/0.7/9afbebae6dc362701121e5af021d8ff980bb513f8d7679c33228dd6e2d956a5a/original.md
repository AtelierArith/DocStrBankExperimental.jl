Black Implied Volatility for European Options

```
	σ=blkimpv(F0,K,r,T,Price,FlagIsCall=true,xtol=1e-14,ytol=1e-15)
```

Where:

```
	F0         = Value of the Forward.
	K          = Strike Price of the Option.
	r          = Zero Rate.
	T          = Time to Maturity of the Option.
	Price      = Price of the Option.
	FlagIsCall = true for Call Options, false for Put Options.

	σ          = implied volatility of the European Option.
```

# Example

```julia-repl
julia> blkimpv(10.0,10.0,0.01,2.0,2.0)
0.36568658096623635
```
