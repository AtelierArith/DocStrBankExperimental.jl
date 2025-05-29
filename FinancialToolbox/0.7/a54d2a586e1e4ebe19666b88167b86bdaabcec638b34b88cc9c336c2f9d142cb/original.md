Black & Scholes Theta for European Options

```
	Θ=blstheta(S0,K,r,T,σ,d=0.0,FlagIsCall=true)
```

Where:

```
	S0         = Value of the Underlying.
	K          = Strike Price of the Option.
	r          = Zero Rate.
	T          = Time to Maturity of the Option.
	σ          = Implied Volatility
	d          = Implied Dividend of the Underlying.
	FlagIsCall = true for Call Options, false for Put Options.

	Θ          = theta of the European Option.
```

# Example

```julia-repl
julia> blstheta(10.0,10.0,0.01,2.0,0.2,0.01)
-0.26273403060652334
```
