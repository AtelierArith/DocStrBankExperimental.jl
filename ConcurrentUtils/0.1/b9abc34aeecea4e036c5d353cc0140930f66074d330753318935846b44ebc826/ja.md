```
try_race_put!(promise::Promise{T}, value) -> Ok(value′::T) or Err(existing::T)
```

`promise`に`value`を設定しようとします。

`value`は最初に`T`に変換されるため、返される`value′`は入力の`value`と同一でない場合があります。

# 拡張ヘルプ

## 例

```jldoctest ConcurrentUtils2
julia> using ConcurrentUtils

julia> p = Promise{Int}();

julia> try_race_put!(p, 123)
Try.Ok: 123

julia> try_race_put!(p, 456)
Try.Err: 123
```
