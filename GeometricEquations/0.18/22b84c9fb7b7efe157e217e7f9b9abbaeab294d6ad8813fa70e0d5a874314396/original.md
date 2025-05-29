`PSDE`: Stratonovich Partitioned Stochastic Differential Equation

A partitioned stochastic differential equations is an initial value problem of the form

$$
\begin{aligned}
dq (t) &= v(t, q(t), p(t)) \, dt + B(t, q(t), p(t)) \circ dW , & q(t_{0}) &= q_{0} , \\
dp (t) &= f(t, q(t), p(t)) \, dt + G(t, q(t), p(t)) \circ dW , & p(t_{0}) &= p_{0}
\end{aligned}
$$

with the drift vector fields $v$ and $f$, diffusion matrices $B$ and $G$, initial conditions $q_{0}$ and $p_{0}$, the dynamical variables $(q,p)$ taking values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$, and the m-dimensional Wiener process W

### Parameters

  * `vType <: Callable`: type of `v`
  * `fType <: Callable`: type of `f`
  * `BType <: Callable`: type of `B`
  * `GType <: Callable`: type of `G`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v`:  function computing the drift vector field for the position variable $q$
  * `f`:  function computing the drift vector field for the momentum variable $p$
  * `B`:  function computing the d x m diffusion matrix for the position variable $q$
  * `G`:  function computing the d x m diffusion matrix for the momentum variable $p$
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
PSDE(v, f, B, G, invariants, parameters, periodicity)
PSDE(v, f, B, G; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

The functions `v`, `f`, `B` and `G`, providing the drift vector fields and diffusion matrices, each take five arguments, `v(v, t, q, p, params)`, `f(f, t, q, p, params)`, `B(B, t, q, p, params)` and `G(G, t, q, p, params)`, where `t` is the current time, `(q, p)` is the current solution, and `v`, `f`, `B` and `G` are the variables which hold the result of evaluating the vector fields $v$, $f$ and the matrices $B$, $G$ on `t` and `(q,p)`, and `params` are optional parameters.

The corresponding methods should have the following signatures:

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function B(B, t, q, p, params)
    B[1,1] = ...
    ...
end

function G(G, t, q, p, params)
    G[1,1] = ...
    ...
end
```
