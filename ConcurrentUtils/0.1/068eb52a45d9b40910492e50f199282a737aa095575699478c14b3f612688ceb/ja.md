```
try_race_put_with!(thunk, promise::Promise{T}) -> Ok(computed::T) or Err(existing::T)
```

既存の値を取得するか、計算された値を設定します（`computed = thunk()`）。`thunk`は、`promise`の各インスタンスに対して最大1回呼び出されます。

# 拡張ヘルプ

## 例

```jldoctest ConcurrentUtils3
julia> using ConcurrentUtils

julia> p = Promise{Int}();

julia> try_race_put_with!(p) do
           123 + 456
       end
Try.Ok: 579

julia> try_race_put_with!(p) do
           42
       end
Try.Err: 579
```
