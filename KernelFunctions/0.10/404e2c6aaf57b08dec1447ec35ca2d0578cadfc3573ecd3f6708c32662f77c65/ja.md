```
PeriodicTransform(f)
```

入力を周波数 `f` の単位円に要素ごとにマッピングする変換です。

この変換が入力に適用されたカーネルを持つGPからのサンプルは、周波数 `f` のサンプルを生成します。

# 例

```jldoctest
julia> f = rand(); t = PeriodicTransform(f); x = rand();

julia> t(x) == [sinpi(2 * f * x), cospi(2 * f * x)]
true
```
