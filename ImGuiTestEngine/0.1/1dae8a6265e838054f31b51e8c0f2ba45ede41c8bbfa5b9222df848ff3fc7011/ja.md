```julia
GetRef(

) -> NamedTuple{(:id, :path), <:Tuple{UInt32, Union{Nothing, String}}}
GetRef(
    ctx
) -> NamedTuple{(:id, :path), <:Tuple{UInt32, Union{Nothing, String}}}

```

現在の参照を取得します。`id` と `path` プロパティを持っています。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    x = GetRef()
    @show x.id x.path
end
```
