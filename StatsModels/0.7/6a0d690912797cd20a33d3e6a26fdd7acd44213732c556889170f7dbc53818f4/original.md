```
FunctionTerm{F,Args} <: AbstractTerm
```

Represents a call to a Julia function.  The first type parameter is the type of the captured function (e.g., `typeof(log)`), and the second is the type of the captured arguments (e.g., a `Vector` of `AbstractTerm`s).

Nested function calls are captured as further `FunctionTerm`s.

# Fields

  * `f::F`: the captured function (e.g., `log`)
  * `args::Args`: the arguments of the call passed to `@formula`, each captured as an `AbstractTerm`.  Usually this is a `Vector{<:AbstractTerm}`.
  * `exorig::Expr`: the original expression passed to `@formula`

# Type parameters

  * `F`: the type of the captured function (e.g., `typeof(log)`)
  * `Args`: the type of container of captured arguments.

# Example

```jldoctest
julia> f = @formula(y ~ log(1 + a + b))
FormulaTerm
Response:
  y(unknown)
Predictors:
  (a,b)->log(1 + a + b)

julia> typeof(f.rhs)
FunctionTerm{typeof(log), Vector{FunctionTerm{typeof(+), Vector{AbstractTerm}}}}

julia> typeof(only(f.rhs.args))
FunctionTerm{typeof(+), Vector{AbstractTerm}}

julia> only(f.rhs.args).args
3-element Vector{AbstractTerm}:
 1
 a(unknown)
 b(unknown)

julia> f.rhs.f(1 + 3 + 4)
2.0794415416798357

julia> modelcols(f.rhs, (a=3, b=4))
2.0794415416798357

julia> modelcols(f.rhs, (a=[3, 4], b=[4, 5]))
2-element Vector{Float64}:
 2.0794415416798357
 2.302585092994046
```
