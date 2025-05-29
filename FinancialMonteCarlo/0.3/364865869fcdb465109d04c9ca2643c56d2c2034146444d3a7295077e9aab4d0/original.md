Low Level Interface for Pricing

```
	Price=pricer(mcProcess,rfCurve,mcConfig,abstractPayoff)
```

Where:

```
	mcProcess      = Process to be simulated.
	rfCurve        = Zero Rate Data.
	mcConfig       = Basic properties of MonteCarlo simulation
	abstractPayoff = Payoff(s) to be priced

	Price          = Price of the derivative
```
