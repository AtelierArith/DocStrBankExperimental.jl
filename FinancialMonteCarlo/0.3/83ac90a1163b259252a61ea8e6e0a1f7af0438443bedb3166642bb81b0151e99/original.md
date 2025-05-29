General Interface for Payoff computation from MonteCarlo paths

```
	Payoff=payoff(S,optionData,rfCurve,T1=optionData.T)
```

Where:

```
	S           = Paths of the Underlying.
	optionData  = Datas of the Option.
	rfCurve     = Datas of the Risk Free Curve.
	T1          =Final Time of Spot Simulation (default equals Time to Maturity of the option)[Optional, default to optionData.T]

	Payoff      = payoff of the Option.
```
