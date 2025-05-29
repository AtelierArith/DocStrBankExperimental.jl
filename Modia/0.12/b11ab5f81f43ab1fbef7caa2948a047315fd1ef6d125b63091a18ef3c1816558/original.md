```
solution = simulate!(instantiatedModel [, algorithm];
          merge            = missing,  # change parameter/init/start values
          tolerance        = 1e-6,     # relative tolerance
          startTime        = 0.0,
          stopTime         = 0.0,      # stopTime >= startTime required
          interval         = missing,  # = (stopTime-startTime)/500
          interp_points    = 0,
          dtmax            = missing,  # = 100*interval
          adaptive         = true,
          nlinearMinForDAE = 10,
          log              = false,
          logStates        = false,
          logEvents        = false,
          logProgress      = false,
          logTiming        = false,
          logParameters    = false,
          logEvaluatedParameters   = false,
          requiredFinalStates      = missing
          requiredFinalStates_rtol = 1e-3,
          requiredFinalStates_atol = 0.0,
          useRecursiveFactorizationUptoSize = 0)
```

Simulate `instantiatedModel::InstantiatedModel` with `algorithm` (= `alg` of [ODE Solvers of DifferentialEquations.jl](https://diffeq.sciml.ai/stable/solvers/ode_solve/) or [DAE Solvers of DifferentialEquations.jl](https://diffeq.sciml.ai/stable/solvers/dae_solve/)).

If the `algorithm` argument is missing, `algorithm=Sundials.CVODE_BDF()` is used, provided instantiatedModel has `FloatType = Float64`. Otherwise, a default algorithm will be chosen from DifferentialEquations (for details see [https://arxiv.org/pdf/1807.06430](https://arxiv.org/pdf/1807.06430), Figure 3). The symbols `CVODE_BDF` and `IDA` are exported from Modia, so that `simulate!(instantiatedModel, CVODE_BDF(), ...)` and `simulate!(instantiatedModel, IDA(), ...)` can be used (instead of `import Sundials; simulate!(instantiatedModel, Sundials.xxx(), ...)`).

The simulation results are stored in `instantiatedModel` and can be plotted with `plot(instantiatedModel, ...)`. The result values can be retrieved with `getValues(..)` for Var(..) and `getValue(..)` for Par(..). `showInfo(instantiatedModel)` prints information about the signals in the result. For more details, see sections [Parameters/Init/Start](@ref), [Results and Plotting](@ref).

The return argument `solution` is the return argument from `DifferentialEquations.solve(..)` and therefore all post-processing functionality from `DifferentialEqautions.jl` can be used. Especially,

  * solution.t[i] # time-instant at storage point i (solution.t[end] = stopTime)
  * solution.u[i] # states at storage point i

A simulation run can be aborted with `<CTRL> C` (SIGINT), provided `using PyPlot` or `import PyPlot` was not called before (the signals in Python module matplotlib.pyplot intervene with Julias signals, see [PyPlot.jl issue 305](https://github.com/JuliaPy/PyPlot.jl/issues/305)).

# Optional ArgumentsS

  * `merge`: Define parameters and init/start values that shall be merged with the previous values          stored in `model`, before simulation is started. If, say, an init value `phi = Var(init=1.0)`          is defined in the model, a different init value can be provided with          `merge = Map(phi=2.0)`.
  * `tolerance`: Relative tolerance.
  * `startTime`: Start time. If value is without unit, it is assumed to have unit [s].
  * `stopTime`: Stop time. If value is without unit, it is assumed to have unit [s].
  * `interval`: Interval to store result. If `interval=missing`, it is internally selected as             (stopTime-startTime)/500.             If value is without unit, it is assumed to have unit [s].
  * `interp_points`: If crossing functions defined, number of additional interpolation points             in one step.
  * `dtmax`: Maximum step size. If `dtmax==missing`, it is internally set to `100*interval`.
  * `adaptive`: = true, if the `algorithm` should use step-size control (if available).             = false, if the `algorithm` should use a fixed step-size of `interval` (if available).
  * `nlinearMinForDAE`: If `algorithm` is a DAE integrator (e.g. `IDA()`) and the size of a linear equation system             is `>= nlinearMinForDAE` and the iteration variables of this equation system are a subset of the             DAE state derivatives, then during continuous integration (but not at events, including             initialization) this equation system is not locally solved but is solved via the DAE integrator.             Typically, for large linear equation systems, simulation efficiency is considerably improved             in such a case.f
  * `log`: = true, to log the simulation.
  * `logStates`: = true, to log the states, its init/start values and its units.
  * `logEvents`: = true, to log events.
  * `logProgress` = true, to printout current simulation time every 5s.
  * `logTiming`: = true, to log the timing with `instantiatedModel.timer` which is an instance              of [TimerOutputs](https://github.com/KristofferC/TimerOutputs.jl).TimerOutput.              A user function can include its timing via
                 `TimerOutputs.@timeit instantiatedModel.timer "My Timing" <statement>`.
  * `logParameters`: = true, to log parameters and init/start values defined in model.
  * `logEvaluatedParameters`: = true, to log the evaluated parameter and init/start values that                           are used for initialization and during simulation.
  * `requiredFinalStates`: is not `missing`: Test with `@test` whether the ODE state vector at the             final time instant is in agreement to vector `requiredFinalStates` with respect             to tolerances `requiredFinalStates_rtol, requiredFinalStates_atol`. If this is not the case, print the             final state vector (so that it can be included with copy-and-paste in the simulate!(..) call).             If you checked that the result of the simulation is correct, use `requiredFinalStates = []` to get             a printout of the required final states and then copy it in your test.
  * `requiredFinalStates_rtol`: Relative tolerance used for `requiredFinalStates`.
  * `requiredFinalStates_atol`: Absolute tolerance used for `requiredFinalStates` (see atol in `?isapprox`)
  * `useRecursiveFactorizationUptoSize`: = 0: Linear equation systems A*v=b are solved with              `RecursiveFactorization.jl` instead of the default `lu!(..)` and `ldiv!(..)`, if              `length(v) <= useRecursiveFactorizationUptoSize`.              According to `RecursiveFactorization.jl` docu, it is faster as `lu!(..)` with OpenBLAS,              for `length(v) <= 500` (typically, more as a factor of two).              Since there had been some cases where `lu!(..)!` was successful,              but `RecursiveFactorization.jl` failed due to a singular system, the default is to use `lu!(..)!`.

# Examples

```julia
using Modia
@usingModiaPlot

# Define model
inputSignal(t) = sin(t)

FirstOrder = Model(
    T = 0.2,
    x = Var(init=0.3),
    equations = :[u = inputSignal(time/u"s"),
                  T * der(x) + x = u,
                  y = 2*x]
)

# Modify parameters and initial values of model
FirstOrder2 = FirstOrder | Map(T = 0.4, x = Var(init=0.6))

# Instantiate model
firstOrder = @instantiateModel(FirstOrder2, logCode=true)


# Simulate with automatically selected algorithm (Sundials.CVODE_BDF())
# and modified parameter and initial values
simulate!(firstOrder, stopTime = 1.0, merge = Map(T = 0.6, x = 0.9), logEvaluatedParameters=true)

# Plot variables "x", "u" in diagram 1, "der(x)" in diagram 2, both diagrams in figure 3
plot(firstOrder, [("x","u"), "der(x)"], figure=3)

# Retrieve "time" and "u" values:
usig = getPlotSignal(firstOrder, "x")
       # usig.xsig      : time vector
       # usig.xsigLegend: legend for time vector
       # usig.ysig      : "x" vector
       # usig.ysigLegend: legend for "x" vector
       # usig.ysigType  : ModiaResult.Continuous or ModiaResult.Clocked

# Simulate with Runge-Kutta 5/4 with step-size control
simulate!(firstOrder, Tsit5(), stopTime = 1.0)

# Simulate with Runge-Kutta 4 with fixed step size
simulate!(firstOrder, RK4(), stopTime = 1.0, adaptive=false)

# Simulate with algorithm that switches between
# Verners Runge-Kutta 6/5 algorithm if non-stiff region and
# Rosenbrock 4 (= A-stable method) if stiff region with step-size control
simulate!(firstOrder, AutoVern6(Rodas4()), stopTime = 1.0)
```
