General Interface for Computation of variance interval of price

```
	variance_=variance(mcProcess,rfCurve,mcConfig,abstractPayoff)
```

Where:

```
	mcProcess      = Process to be simulated.
	rfCurve        = Zero Rate Data.
	mcConfig       = Basic properties of MonteCarlo simulation
	abstractPayoff = Payoff(s) to be priced

	variance_      = variance of the payoff of the derivative
```
