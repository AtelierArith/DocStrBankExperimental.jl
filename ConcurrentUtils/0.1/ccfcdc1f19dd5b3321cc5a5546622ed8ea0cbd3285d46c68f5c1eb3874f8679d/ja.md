```
try_race_fetch(promiselike) -> Ok(value::T) or Err(NotSetError())
```

設定されている場合は `value` を取得しようとします。成功した場合は `Ok(value)` を返し、失敗した場合は `Err(NotSetError())` を返します。

`try_race_fetch` は [`Promise`](@ref) またはタスクレット ([`@tasklet`](@ref)) で呼び出すことができます。

# 拡張ヘルプ

## 例

```jldoctest try_race_fetch
julia> using ConcurrentUtils

julia> p = Promise{Int}();

julia> try_race_fetch(p)
Try.Err: NotSetError()

julia> put!(p, 123);

julia> try_race_fetch(p)
Try.Ok: 123
```
