```
SaddleSystem
```

Construct a saddle-point system operator from the constituent operator blocks. The resulting object can be used with `*` and `\` to multiply and solve. The saddle-point problem has the form

$\begin{bmatrix}A & B_1^T \\ B_2 & C \end{bmatrix} \begin{pmatrix} u \\ f \end{pmatrix} = \begin{pmatrix} r_1 \\ r_2 \end{pmatrix}$

### Constructors

`SaddleSystem(A::AbstractMatrix,B₂::AbstractMatrix,B₁ᵀ::AbstractMatrix,C::AbstractMatrix[,eltype=Float64])`. Blocks are given as matrices. Must have consistent sizes to stack appropriately. If this is called with `SaddleSystem(A,B₂,B₁ᵀ)`, it sets `C` to zero automatically.

`SaddleSystem(A,B₂,B₁ᵀ,C,u,f[,eltype=Float64])`. Operators `A`, `B₂`, `B₁ᵀ`, `C` are given in various forms, including matrices, functions, and function-like objects. `u` and `f` are examples of the data types in the corresponding solution and right-hand side vectors. Guidelines:

  * The entries `A` and `B₂` must be able to act upon `u` (either by multiplication or as a function) and `B₁ᵀ` and `C` must be able to act on `f` (also, either by multiplication or as a function).
  * `A` and `B₁ᵀ` should return data of type `u`, and `B₂` and `C` should return data of type `f`.
  * `A` must be invertible and be outfitted with operators ``and`ldiv!`.
  * Both `u` and `f` must be subtypes of `AbstractArray`: they must be equipped with `size` and `vec` functions and with a constructor of the form `T(data)` where `T` is the data type of `u` or `f` and `data` is the wrapped data array.

If called as `SaddleSystem(A,B₂,B₁ᵀ,u,f)`, the `C` block is omitted and assumed to be zero.

If called with `SaddleSystem(A,u)`, this is equivalent to calling `SaddleSystem(A,nothing,nothing,u,[])`, then this reverts to the unconstrained system described by operator `A`.

The list of vectors `u` and `f` in any of these constructors can be bundled together as a [`SaddleVector`](@ref), e.g. `SaddleSystem(A,B₂,B₁ᵀ,SaddleVector(u,f))`.

An optional keyword argument `solver=` can be used to specify the type of solution for the Schur complement system. By default, this is set to `Direct`, and the Schur complement matrix is formed, factorized, and stored. This can be changed to a variety of iterative solvers, e.g.  `BiCGStabl`, `CG`, `GMRES`, in which case  an iterative solver from [`IterativeSolvers.jl`](https://github.com/JuliaLinearAlgebra/IterativeSolvers.jl)  is used.
