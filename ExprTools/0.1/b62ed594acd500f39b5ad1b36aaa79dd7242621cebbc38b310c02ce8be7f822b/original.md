```
signature(sig::Type{<:Tuple})
```

Like `ExprTools.signature(::Method)` but on the underlying signature type-tuple, rather than the Method`. For`sig`being a tuple-type representing a methods type signature, this generates a dictionary that can be passes to`ExprTools.combinedef`to define that function, Provided that you assign the`:body` key on the dictionary first.

The quality of the output, in terms of matching names etc is not as high as for the `signature(::Method)`, but all the key information is present; and the type-tuple is for other purposes generally easier to manipulate.

Examples

```julia
julia> signature(Tuple{typeof(identity), Any})
Dict{Symbol, Any} with 2 entries:
  :name => :(op::typeof(identity))
  :args => Expr[:(x1::Any)]

julia> signature(Tuple{typeof(+), Vector{T}, Vector{T}} where T<:Number)
Dict{Symbol, Any} with 3 entries:
  :name        => :(op::typeof(+))
  :args        => Expr[:(x1::Array{var"##T#5492", 1}), :(x2::Array{var"##T#5492", 1})]
  :whereparams => Any[:(var"##T#5492" <: Number)]
```

# keywords

  * `extra_hygiene=false`: if set to `true` this forces name-hygine on the `TypeVar`s in  `UnionAll`s, regenerating each with a unique name via `gensym`. This shouldn't actually be required as they are scoped such that they are not supposed to leak. However, there is a long-standing [julia bug](https://github.com/JuliaLang/julia/issues/39876) that means  they do leak if they clash with function type-vars.
