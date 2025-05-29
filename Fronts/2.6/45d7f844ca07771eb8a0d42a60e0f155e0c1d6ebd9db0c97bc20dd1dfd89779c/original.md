```
boltzmann(prob::CauchyProblem) -> DifferentialEquations.ODEProblem
boltzmann(prob::SorptivityCauchyProblem) -> DifferentialEquations.ODEProblem
```

Transform `prob` into an ODE problem in terms of the Boltzmann variable `o`.

The ODE problem is set up to terminate automatically (with `.retcode == ReturnCode.Success`) when the steady state is reached.

See also: [`DifferentialEquations`](https://diffeq.sciml.ai/stable/)
