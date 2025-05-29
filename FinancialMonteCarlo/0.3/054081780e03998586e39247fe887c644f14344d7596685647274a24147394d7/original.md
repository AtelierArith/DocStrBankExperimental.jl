General Interface for Delta

```
	Delta=delta(mcProcess,rfCurve,mcConfig,abstractPayoff,dS0)
```

Where:

```
	mcProcess      = Process to be simulated.
	rfCurve        = Zero Rate Data.
	mcConfig       = Basic properties of MonteCarlo simulation
	abstractPayoff = Payoff(s) to be priced
	dS0            = increment [optional, default to 1e-7]
	
	Delta          = Delta of the derivative
```
