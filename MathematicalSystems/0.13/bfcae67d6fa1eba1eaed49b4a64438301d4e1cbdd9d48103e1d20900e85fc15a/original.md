```
system(expr...)
```

Return an instance of the system type corresponding to the given expressions.

### Input

  * `expr` – expressions separated by commas which define the dynamic equation,           the constraint sets or the dimensionality of the system

### Output

A system that best matches the given expressions.

### Notes

**Terms.** The expression `expr` contains one or more of the following sub-expressions:

  * dynamic equation, either continuous, e.g.`x' = Ax`, or discrete, e.g. `x⁺ = Ax`
  * set constraints, e.g. `x ∈ X`
  * input constraints, e.g. `u ∈ U`
  * dimensionality, e.g. `dim: (2,1)` or `dim = 1`
  * specification of the input variable, e.g. `input: u` or `input = u`
  * specification of the noise variable, e,g, `noise: w` or `noise = w`

The macro call is then formed by separating the previous sub-expressions (which we simply call *terms* hereafter), as in:

```julia
@system(dynamic eq., set constr., input constr., input specif., noise spec., dimens.)
```

The different terms that compose the system's definition do not have to appear in any particular order. Moreover, the only mandatory term is the dynamic equation; the other terms are optional and default values may apply depending on the system type; this is explained next.

**Dynamic equation.** The time derivative in a continuous system is specified by using `'`, as in `x' = A*x`. A discrete system is specified using `⁺` (which can be written with the combination of keys `\^+[TAB]`), as in `x⁺ = A*x`. Moreover, the asterisk denoting matrix-vector products is optional. For instance, both `x' = Ax` and `x' = A*x` are parsed as the linear continuous system whose state matrix is `A`. The matrix is supposed to be defined at the call site.

**Default values.** When the dynamic equation is parsed, the variable on the left-hand side is interpreted as the state variable. The input variable is by default `u` and the noise variable is by default `w`. If we want to change the default name of the input variable, this can be done by adding the term `input: var` (or equivalently, `input=var)` where `var` corresponds to the new name of the input variable, eg. `@system(x' = A*x + B*v, input:v)`. Similarly, a noise variable is specified with `noise: var` or `noise=var`.

**Exceptions.** The following exceptions and particular cases apply:

  * If the right-hand side has the form `A*x + B*foo`, `A*x + B*foo + c` or `f(x, foo)`, the equation is parsed as a controlled linear (affine) or controlled black-box system with input `foo`. Note that in this case, `input` variable does not correspond to the default value of `u`, but `foo` is parsed as being the input.
  * If the left-hand side contains a multiplicative term in the form `E*x⁺` or `E*x'`, the equation is parsed as an algebraic equation and hence gives rise to a descriptor system. In this case, the asterisk `*` operator is mandatory.
  * Systems of the form `x' = α*x` where `α` is a scalar are parsed as linear systems. The default dimension is `1` and `α` is parsed as `Float64`; if the system is higher-dimensional, use `dim`, as in `x' = 2x, dim=3`.

### Examples

Let us first create a continuous linear system using this macro:

```jldoctest system_macro
julia> A = [1. 0; 0 1.];

julia> @system(x' = A*x)
LinearContinuousSystem{Float64, Matrix{Float64}}([1.0 0.0; 0.0 1.0])
```

A discrete system is defined by using `⁺`:

```jldoctest system_macro
julia> @system(x⁺ = A*x)
LinearDiscreteSystem{Float64, Matrix{Float64}}([1.0 0.0; 0.0 1.0])
```

Additionally, a set definition `x ∈ X` can be added to create a constrained system. For example, a discrete controlled affine system with constrained states and inputs writes as:

```jldoctest system_macro
julia> using LazySets

julia> B = Matrix([1.0 0.5]');

julia> c = [1.0, 1.5];

julia> X = BallInf(zeros(2), 10.0);

julia> U = BallInf(zeros(1), 2.0);

julia> @system(x' = A*x + B*u + c, x ∈ X, u ∈ U)
ConstrainedAffineControlContinuousSystem{Float64, Matrix{Float64}, Matrix{Float64}, Vector{Float64}, BallInf{Float64, Vector{Float64}}, BallInf{Float64, Vector{Float64}}}([1.0 0.0; 0.0 1.0], [1.0; 0.5;;], [1.0, 1.5], BallInf{Float64, Vector{Float64}}([0.0, 0.0], 10.0), BallInf{Float64, Vector{Float64}}([0.0], 2.0))
```

For the creation of a black-box system, the state, input and noise dimensions have to be defined separately. For a constrained controlled black-box system, the macro writes as

```jldoctest system_macro
julia> f(x, u) = x + u;

julia> @system(x⁺ = f(x, u), x ∈ X, u ∈ U, dim: (2,2))
ConstrainedBlackBoxControlDiscreteSystem{typeof(f), BallInf{Float64, Vector{Float64}}, BallInf{Float64, Vector{Float64}}}(f, 2, 2, BallInf{Float64, Vector{Float64}}([0.0, 0.0], 10.0), BallInf{Float64, Vector{Float64}}([0.0], 2.0))
```
