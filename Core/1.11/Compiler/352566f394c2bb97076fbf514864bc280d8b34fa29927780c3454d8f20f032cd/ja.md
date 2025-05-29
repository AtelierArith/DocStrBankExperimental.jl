```
BackedgeIterator(backedges::Vector{Any})
```

バックエッジのリストに対するイテレータを返します。イテレーションは `(sig, caller)` 要素を返し、以下のいずれかになります：

  * `BackedgePair(nothing, caller::MethodInstance)`：通常の推論可能なディスパッチによって行われた呼び出し
  * `BackedgePair(invokesig::Type, caller::MethodInstance)`：`invoke(f, invokesig, args...)` によって行われた呼び出し
  * `BackedgePair(specsig::Type, mt::MethodTable)`：抽象呼び出し

# 例

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
