```
@forward_methods T [field=_field] [map=_map] methods...
```

Forwards the method definitions for `x::T`, depending on the value of `_field`. 

`_field` must be one of the following expressions

  * `k::Symbol` or `k::QuoteNode`, or an expression of the form `getfield(_, k)`, in which case methods will be forwarded to `getfield(x, k)`
  * an expression of the form `a.b.c. ...`, in which case methods will be forwarded to `getfield(getfield(getfield(x, :a), :b), :c) ...`
  * an expression of the form `getproperty(_, k)`, in which case methods will be forwarded to `getproperty(x, k)`
  * an expression of the form `t[args...]`, in which case methods will be forwarded to `x[args...]`
  * or an expression of the form `f(_)` for a single-argument function `f`, in which case methods will be forwarded to `f(x)`

For notational purposes below, call the forwarded value `forwarded_value(x)`. 

Each `method` must be one of the following expressions 

  * an expression of the form `f::Symbol` or `A.f`, which will forward the single-argument function `f(x)` or `A.f(x)` to `f(forwarded_value(x))` or `A.f(forwarded_value(x))`, respectively
  * a function signature of the form `f(args...)`, or `f(args...; kwargs...)`. In this form, there must be either exactly one expression of  the form `x::T` or `_` (an underscore) in `args`. If this occurs at position `i`, say, this macro will forward this method to the definition

    `f(args[1], args[2], ..., args[i-1], forwarded_value(x), args[i+1], ..., args[end]; kwargs...)`

    When `field` maps to invoking `getfield` for field `k`, one can also write an argument expression of the form `::T` or `x::T`. In this case, this macro definition will define

    `f(args[1], ..., args[i-1], ::Type{T}, args[i+1], ..., args[end]; kwargs) = f(args[1], ..., args[i-1], fieldtype(T, k), args[i+1], ..., args[end]; kwargs)`

    which can be useful for forwarding, for instance, trait-based methods to the corresponding container type.

Each `method` may also be a `:block` expression, where each sub-expression satisfies one of the above conditions

## Optional Arguments

The optional `map=_map` parameter allows you to apply an expression transformation to the resulting forwarded expression. `_map` must be an expression containing at least one underscore `_` placeholder and optionally `_obj` placeholders. `_` and `_obj` will be replaced with the transformed function and initial object argument, respectively. 

For example, if we have 

```julia
    struct LockableDict{K,V}
        d::Dict{K,V}
        lock::ReentrantLock
    end
    @forward LockableDict{K,V} field=lock Base.lock Base.unlock
    @forward LockableDict{K,V} field=d map=(begin lock(_obj); try _ finally unlock(_obj) end end) Base.getindex(_, k) 
```

Then the expressions generated in the second statement are (roughly) of the form 

```julia
    function Base.getindex(l::LockableDict{K,V}, k)
        lock(l)
        try 
            Base.getindex(getfield(l, :d))
        finally
            unlock(l)
        end
    end
```

# Notes

  * Parametric expressions are supported for `T`, as well as for the function signature form of `method`

# Examples

```julia-repl
julia> struct B{T} 
         v::Vector{T}
       end

julia> @forward_methods B{T} field=v Base.firstindex Base.lastindex Base.getindex(_, k::Int) Base.setindex!(x::B, v, k) (Base.eachindex(x::B{T}) where {T})

julia> b = B([1,2,3])
B{Int64}([1, 2, 3])

julia> for i in eachindex(b)
         b[i] = b[i]^2
       end
julia> b[end]
9

julia> struct C
         d::Dict{String,Int}
       end
julia> @forward_methods C field=d Base.keytype(::Type{C}) Base.valtype(::Type{C})

julia> keytype(C)
String 

julia> valtype(C)
Int
```
