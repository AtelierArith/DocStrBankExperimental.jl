```
groupunique([by], [f], iter)
```

`by(x)` でグループ化された `iter` の要素 `x` の集合をマッピングし、値は `f(x)` となる辞書を返します。ここで、`by` と `f` はデフォルトで恒等関数になります。

これは `unique.(group(by, f, iter))` に似ていますが、各サブグループは異なる値の `AbstractIndices` であり（繰り返しの可能性がある `AbstractArray` ではありません）。

# 例

```julia
julia> groupunique(iseven, [1,2,1,2,3])
2-element Dictionary{Bool,Indices{Int64}}
 false │ {2}
  true │ {1, 3}
```
