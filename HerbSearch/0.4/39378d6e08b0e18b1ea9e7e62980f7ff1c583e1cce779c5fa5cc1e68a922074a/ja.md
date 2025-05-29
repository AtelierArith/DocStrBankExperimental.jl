```
sample(::Type{NodeLoc}, root::RuleNode, maxdepth::Int=typemax(Int))
```

最大深度がmaxdepthを超えないように木の中からランダムなノードを均等に選択します。サブツリーを置き換えられるように親を使用して位置を指定する[`NodeLoc`](@ref)を返します。
