`SPSDE`: Stratonovich Split Partitioned Stochastic Differential Equation

Defines a partitioned stochastic differential initial value problem

$$
\begin{aligned}
dq (t) &=   v(t, q(t), p(t)) \, dt + B(t, q(t), p(t)) \circ dW , & q(t_{0}) &= q_{0} , \\
dp (t) &= [ f_1(t, q(t), p(t)) + f_2(t, q(t), p(t)) ] \, dt + [ G_1(t, q(t), p(t)) + G_2(t, q(t), p(t)) ] \circ dW , & p(t_{0}) &= p_{0} ,
\end{aligned}
$$

with the drift vector fields $v$ and $f_i$, diffusion matrices $B$ and $G_i$, initial conditions $q_{0}$ and $p_{0}$, the dynamical variables $(q,p)$ taking values in $\mathbb{R}^{d} \times \mathbb{R}^{d}$, and the m-dimensional Wiener process W

### Parameters

  * `vType <: Function`: type of `v`
  * `f1Type <: Function`: type of `f1`
  * `f2Type <: Function`: type of `f2`
  * `BType <: Function`: type of `B`
  * `G1Type <: Function`: type of `G1`
  * `G2Type <: Function`: type of `G2`
  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

### Fields

  * `v` :  function computing the drift vector field for the position variable $q$
  * `f1`:  function computing the drift vector field for the momentum variable $p$
  * `f2`:  function computing the drift vector field for the momentum variable $p$
  * `B` :  function computing the d x m diffusion matrix for the position variable $q$
  * `G1`:  function computing the d x m diffusion matrix for the momentum variable $p$
  * `G2`:  function computing the d x m diffusion matrix for the momentum variable $p$
  * `invariants`: functions for the computation of invariants, either a `NamedTuple` containing the equation's invariants or `NullInvariants`
  * `parameters`: type constraints for parameters, either a `NamedTuple` containing the equation's parameters or `NullParameters`
  * `periodicity`: determines the periodicity of the state vector `q` for cutting periodic solutions, either a `AbstractArray` or `NullPeriodicity`

### Constructors

```julia
SPSDE(v, f1, f2, B, G1, G2, invariants, parameters, periodicity)
SPSDE(v, f1, f2, B, G1, G2; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

The functions `v`, `f1`, `f2`, `B`, `G1` and `G2`, providing the drift vector fields and diffusion matrices, all take five arguments, `(out, t, q, p, params)`.

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f1(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function f2(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function B(B, t, q, p, params)
    B[1,1] = ...
    ...
end

function G1(G, t, q, p, params)
    G[1,1] = ...
    ...
end

function G2(G, t, q, p, params)
    G[1,1] = ...
    ...
end
```

where `t` is the current time, `(q,p)` is the current solution vector, and `v`, `f`, `B` and `G` are the variables which hold the result of evaluating the vector fields $v$, $f$ and the matrices $B_i$, $G_i$ on `(t,q,p)`.
