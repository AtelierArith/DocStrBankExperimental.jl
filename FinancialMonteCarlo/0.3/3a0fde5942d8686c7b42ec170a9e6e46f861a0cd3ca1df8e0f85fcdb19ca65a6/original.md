General Interface for Computation of confidence interval of price

```
	IC=confinter(mcProcess,rfCurve,mcConfig,abstractPayoff,alpha)
```

Where:

```
	mcProcess      = Process to be simulated.
	rfCurve        = Zero Rate Data.
	mcConfig       = Basic properties of MonteCarlo simulation
	abstractPayoff = Payoff(s) to be priced
	alpha          = confidence level [Optional, default to 99%]

	Price          = Price of the derivative
```
