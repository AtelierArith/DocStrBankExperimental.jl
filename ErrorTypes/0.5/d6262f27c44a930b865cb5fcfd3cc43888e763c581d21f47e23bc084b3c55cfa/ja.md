```
@?(expr)
```

`Err` 値を外部関数に伝播させる `Result` を返します。`expr` を評価し、`Result` を返す必要があります。もし `Ok` 値 `x` を含む場合、ラップされていない値 `x` に評価されます。そうでなければ、`return Err(x)` に評価されます。

# 例

```jldoctest
julia> (f(x::Option{T})::Option{T}) where T = Ok(@?(x) + one(T));

julia> f(some(1.0)), f(none(Int))
(some(2.0), none(Int64))
```
