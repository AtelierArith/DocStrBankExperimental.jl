```
setindex(t::Tuple, v, i::Integer)
```

新しいタプルを作成し、`t`に似ており、インデックス`i`の値を`v`に設定します。範囲外の場合は`BoundsError`をスローします。

# 例

```jldoctest
julia> Base.setindex((1, 2, 6), 2, 3) == (1, 2, 2)
true
```
