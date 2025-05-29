```
race_put_with!(thunk, promise::Promise{T}) -> value::T
```

既存の `value` を取得するか、`value = thunk()` を設定します。`thunk` は各 `promise` のインスタンスごとに最大1回呼び出されます。

これは [`try_race_put_with!`](@ref) に似ていますが、呼び出し元は戻り値の型によって `thunk` が呼び出されたかどうかを判断できません。

# 拡張ヘルプ

## 例

```jldoctest ConcurrentUtils1
julia> using ConcurrentUtils

julia> p = Promise{Int}();

julia> race_put_with!(p) do
           println("called")
           123 + 456
       end
called
579

julia> race_put_with!(p) do
           println("called")
           42
       end
579
```
