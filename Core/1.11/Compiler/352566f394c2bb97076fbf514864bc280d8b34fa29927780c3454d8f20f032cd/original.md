```
BackedgeIterator(backedges::Vector{Any})
```

Return an iterator over a list of backedges. Iteration returns `(sig, caller)` elements, which will be one of the following:

  * `BackedgePair(nothing, caller::MethodInstance)`: a call made by ordinary inferable dispatch
  * `BackedgePair(invokesig::Type, caller::MethodInstance)`: a call made by `invoke(f, invokesig, args...)`
  * `BackedgePair(specsig::Type, mt::MethodTable)`: an abstract call

# Examples

```julia
julia> callme(x) = x+1
callme (generic function with 1 method)

julia> callyou(x) = callme(x)
callyou (generic function with 1 method)

julia> callyou(2.0)
3.0

julia> mi = which(callme, (Any,)).specializations
MethodInstance for callme(::Float64)

julia> @eval Core.Compiler for (; sig, caller) in BackedgeIterator(Main.mi.backedges)
           println(sig)
           println(caller)
       end
nothing
callyou(Float64) from callyou(Any)
```
