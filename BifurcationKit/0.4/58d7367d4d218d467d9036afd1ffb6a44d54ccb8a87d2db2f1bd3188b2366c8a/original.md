```julia
struct PeriodicOrbitTrapProblem{Tprob, vectype, Tls<:BifurcationKit.AbstractLinearSolver, T, Tmass} <: BifurcationKit.AbstractPOFDProblem
```

This composite type implements Finite Differences based on a Trapezoidal rule (Order 2 in time) to locate periodic orbits. More details (maths, notations, linear systems) can be found [here](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/periodicOrbitTrapeze/).

The scheme is as follows. We first consider a partition of $[0,1]$ given by $0<s_0<\cdots<s_m=1$ and one looks for `T = x[end]` such that

$M_a\cdot\left(x_{i} - x_{i-1}\right) - \frac{T\cdot h_i}{2} \left(F(x_{i}) + F(x_{i-1})\right) = 0,\ i=1,\cdots,m-1$

with $u_{0} := u_{m-1}$ and the periodicity condition $u_{m} - u_{1} = 0$ and

where $h_1 = s_i-s_{i-1}$. $M_a$ is a mass matrix. Finally, the phase of the periodic orbit is constrained by using a section (but you could use your own)

$\sum_i\langle x_{i} - x_{\pi,i}, \phi_{i}\rangle=0.$

## Fields

  * `prob_vf::Any`: a bifurcation problem Default: nothing
  * `ϕ::Any`: used to set a section for the phase constraint equation, of size N*M Default: nothing
  * `xπ::Any`: used in the section for the phase constraint equation, of size N*M Default: nothing
  * `M::Int64`: number of time slices Default: 0
  * `mesh::BifurcationKit.TimeMesh`: Mesh, see `TimeMesh` Default: TimeMesh(M)
  * `N::Int64`: dimension of the problem in case of an `AbstractVector` Default: 0
  * `linsolver::BifurcationKit.AbstractLinearSolver`: linear solver for each time slice, i.e. to solve `J⋅sol = rhs`. This is only needed for the computation of the Floquet multipliers in a full matrix-free setting. Default: DefaultLS()
  * `ongpu::Bool`: whether the computation takes place on the gpu (Experimental) Default: false
  * `isautonomous::Bool`: Default: true
  * `massmatrix::Any`: a mass matrix. You can pass for example a sparse matrix. Default: identity matrix. Default: nothing
  * `update_section_every_step::UInt64`: updates the section every `update_section_every_step` step during continuation Default: 1
  * `jacobian::Symbol`: symbol which describes the type of jacobian used in Newton iterations (see below). Default: :Dense

## Constructors

The structure can be created by calling `PeriodicOrbitTrapProblem(;kwargs...)`. For example, you can declare such a problem without vector field by doing

```
PeriodicOrbitTrapProblem(M = 100)
```

# Orbit guess

You will see below that you can evaluate the residual of the functional (and other things) by calling `pb(orbitguess, p)` on an orbit guess `orbitguess`. Note that `orbitguess` must be a vector of size M * N + 1 where N is the number of unknowns in the state space and `orbitguess[M*N+1]` is an estimate of the period $T$ of the limit cycle. More precisely, using the above notations, `orbitguess` must be $orbitguess = [x_{1},x_{2},\cdots,x_{M}, T]$.

Note that you can generate this guess from a function solution using `generate_solution` or `generate_ci_problem`.

# Functional

A functional, hereby called `G`, encodes this problem. The following methods are available

  * `pb(orbitguess, p)` evaluates the functional G on `orbitguess`
  * `pb(orbitguess, p, du)` evaluates the jacobian `dG(orbitguess).du` functional at `orbitguess` on `du`
  * `pb(Val(:JacFullSparse), orbitguess, p)` return the sparse matrix of the jacobian `dG(orbitguess)` at `orbitguess` without the constraints. It is called `A_γ` in the docs.
  * `pb(Val(:JacFullSparseInplace), J, orbitguess, p)`. Same as `pb(Val(:JacFullSparse), orbitguess, p)` but overwrites `J` inplace. Note that the sparsity pattern must be the same independently of the values of the parameters or of `orbitguess`. In this case, this is significantly faster than `pb(Val(:JacFullSparse), orbitguess, p)`.
  * `pb(Val(:JacCyclicSparse), orbitguess, p)` return the sparse cyclic matrix Jc (see the docs) of the jacobian `dG(orbitguess)` at `orbitguess`
  * `pb(Val(:BlockDiagSparse), orbitguess, p)` return the diagonal of the sparse matrix of the jacobian `dG(orbitguess)` at `orbitguess`. This allows to design Jacobi preconditioner. Use `blockdiag`.

# Jacobian

Specify the choice of the jacobian (and linear algorithm), `jacobian` must belong to `[:FullLU, :FullSparseInplace, :Dense, :DenseAD, :BorderedLU, :BorderedSparseInplace, :FullMatrixFree, :BorderedMatrixFree, :FullMatrixFreeAD]`. This is used to select a way of inverting the jacobian `dG` of the functional G.

  * For `jacobian = :FullLU`, we use the default linear solver based on a sparse matrix representation of `dG`. This matrix is assembled at each newton iteration. This is the default algorithm.
  * For `jacobian = :FullSparseInplace`, this is the same as for `:FullLU` but the sparse matrix `dG` is updated inplace. This method allocates much less. In some cases, this is significantly faster than using `:FullLU`. Note that this method can only be used if the sparsity pattern of the jacobian is always the same.
  * For `jacobian = :Dense`, same as above but the matrix `dG` is dense. It is also updated inplace. This option is useful to study ODE of small dimension.
  * For `jacobian = :DenseAD`, evaluate the jacobian using ForwardDiff
  * For `jacobian = :BorderedLU`, we take advantage of the bordered shape of the linear solver and use a LU decomposition to invert `dG` using a bordered linear solver.
  * For `jacobian = :BorderedSparseInplace`, this is the same as for `:BorderedLU` but the cyclic matrix `dG` is updated inplace. This method allocates much less. In some cases, this is significantly faster than using `:BorderedLU`. Note that this method can only be used if the sparsity pattern of the jacobian is always the same.
  * For `jacobian = :FullMatrixFree`, a matrix free linear solver is used for `dG`: note that a preconditioner is very likely required here because of the cyclic shape of `dG` which affects negatively the convergence properties of GMRES.
  * For `jacobian = :BorderedMatrixFree`, a matrix free linear solver is used but for `Jc` only (see docs): it means that `options.linsolver` is used to invert `Jc`. These two Matrix-Free options thus expose different part of the jacobian `dG` in order to use specific preconditioners. For example, an ILU preconditioner on `Jc` could remove the constraints in `dG` and lead to poor convergence. Of course, for these last two methods, a preconditioner is likely to be required.
  * For `jacobian = :FullMatrixFreeAD`, the evaluation map of the differential is derived using automatic differentiation. Thus, unlike the previous two cases, the user does not need to pass a Matrix-Free differential.

!!! note "GPU call"
    For these methods to work on the GPU, for example with `CuArrays` in mode `allowscalar(false)`, we face the issue that the function `_extract_period_fdtrap` won't be well defined because it is a scalar operation. Note that you must pass the option `ongpu = true` for the functional to be evaluated efficiently on the gpu.

