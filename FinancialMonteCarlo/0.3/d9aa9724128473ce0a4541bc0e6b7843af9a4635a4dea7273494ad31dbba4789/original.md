General Interface for Rho computation

```
	Rho=rho(mcProcess,rfCurve,mcConfig,abstractPayoff,dr)
```

Where:

```
	mcProcess      = Process to be simulated.
	rfCurve        = Zero Rate Data.
	mcConfig       = Basic properties of MonteCarlo simulation
	abstractPayoff = Payoff(s) to be priced
	dr             = increment [optional, default to 1e-7]

	Rho            = Rho of the derivative
```
