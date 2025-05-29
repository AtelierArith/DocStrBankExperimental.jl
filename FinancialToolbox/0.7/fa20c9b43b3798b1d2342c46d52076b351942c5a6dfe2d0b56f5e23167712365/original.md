Black & Scholes Rho for European Options

```
	ρ=blsrho(S0,K,r,T,σ,d=0.0,FlagIsCall=true)
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

	ρ          = rho of the European Option.
```

# Example

```julia-repl
julia> blsrho(10.0,10.0,0.01,2.0,0.2,0.01)
8.699626722294234
```
