```
SimulatorLikelihood{distType,obsType,dataType,priorType}
```

Represents a simulator-based likelihood function. A `SimulatorLikelihood` consists of four basic components:

(1) A distribution type, e.g. `Normal`,

(2) A `SimulatorObservable` which represents the observation operator,

(3) A set of `data`, usually a `Vector` or `Matrix`, which matches the structure of the observable,

(4) A prior distribution governing one or more additional parameters required to compute the likelihood.

Due to the typically high cost of evaluating the parameter forward map, `SimulatorLikelihood` effectively decouples the computation of the likelihood from the simulator via the `SimulatorObservable`, which stores the result of a forward simulation. When the `SimulatorLikelihood` is evaluated, these outputs are obtained from `getvalue(obs)` and the only additional parameters needed are those specified by `prior`.
