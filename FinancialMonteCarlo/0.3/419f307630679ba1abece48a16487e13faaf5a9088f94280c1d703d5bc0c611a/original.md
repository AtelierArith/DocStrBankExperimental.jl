General Interface for Stochastic Process simulation

```
	S=simulate(mcProcess,zeroCurve,mcBaseData,T)
```

Where:

```
	mcProcess   = Process to be simulated.
	zeroCurve   = Datas of the Zero Rate Curve.
	mcBaseData  = Basic properties of MonteCarlo simulation
	T           = Final time of the process

	S           = Matrix with path of underlying.
```
