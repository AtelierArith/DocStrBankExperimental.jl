```
FunctionTerm{Forig,Fanon,Names} <: AbstractTerm
```

Represents a call to a Julia function.  The first type parameter is the type of the function as originally specified (e.g., `typeof(log)`), while the second is the type of the anonymous function that will be applied element-wise to the data table.

The `FunctionTerm` *also* captures the arguments of the original call and parses them *as if* they were part of a special DSL call, applying the rules to expand `*`, distribute `&` over `+`, and wrap symbols in `Term`s.

By storing the original function as a type parameter *and* pessimistically parsing the arguments as if they're part of a special DSL call, this allows custom syntax to be supported with minimal extra effort.  Packages can dispatch on `apply_schema(f::FunctionTerm{typeof(special_syntax)}, schema, ::Type{<:MyModel})` and pull out the arguments parsed as terms from `f.args_parsed` to construct their own custom terms.

# Fields

  * `forig::Forig`: the original function (e.g., `log`)
  * `fanon::Fanon`: the generated anonymous function (e.g., `(a, b) -> log(1+a+b)`)
  * `exorig::Expr`: the original expression passed to `@formula`
  * `args_parsed::Vector`: the arguments of the call passed to `@formula`, each parsed *as if* the call was a "special" DSL call.

# Type parameters

  * `Forig`: the type of the original function (e.g., `typeof(log)`)
  * `Fanon`: the type of the generated anonymous function
  * `Names`: the names of the arguments to the anonymous function (as a `NTuple{N,Symbol}`)

# Example

```jldoctest
julia> f = @formula(y ~ log(1 + a + b))
FormulaTerm
Response:
  y(unknown)
Predictors:
  (a,b)->log(1 + a + b)

julia> typeof(f.rhs)
FunctionTerm{typeof(log),var"#1#2",(:a, :b)}

julia> f.rhs.forig(1 + 3 + 4)
2.0794415416798357

julia> f.rhs.fanon(3, 4)
2.0794415416798357

julia> modelcols(f.rhs, (a=3, b=4))
2.0794415416798357

julia> modelcols(f.rhs, (a=[3, 4], b=[4, 5]))
2-element Array{Float64,1}:
 2.0794415416798357
 2.302585092994046
```
