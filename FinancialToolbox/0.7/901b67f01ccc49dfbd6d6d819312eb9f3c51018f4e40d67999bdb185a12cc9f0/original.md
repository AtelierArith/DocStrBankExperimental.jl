Black Price for Binary European Options

```
	Price=blsbin(S0,K,r,T,σ,FlagIsCall=true)
```

Where:

```
	F0         = Value of the Forward.
	K          = Strike Price of the Option.
	r          = Zero Rate.
	T          = Time to Maturity of the Option.
	σ          = Implied Volatility.
	FlagIsCall = true for Call Options, false for Put Options.

	Price      = price of the Binary European Option.
```

# Example

```julia-repl
julia> blsbin(10.0,10.0,0.01,2.0,0.2)
0.4624714677292208
```
