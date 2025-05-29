```
vmeasure(a, b; [β = 1.0]) -> Float64
```

2つのクラスタリング間のV-measure。

`a`と`b`は、[`ClusteringResult`](@ref)インスタンスまたは割り当てベクトル（`AbstractVector{<:Integer}`）のいずれかです。

`β`パラメータは、*均質性*と*完全性*の間のトレードオフを定義します：

  * $$
    β > 1
    $$

    の場合、*完全性*がより強く重視されます、
  * $$
    β < 1
    $$

    の場合、*均質性*がより強く重視されます。

# 参考文献

> Andrew Rosenberg and Julia Hirschberg, 2007. *V-Measure: A conditional entropy-based external cluster evaluation measure*

