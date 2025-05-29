```
getparams(m::RheoModel; unicode=true)
```

`getparams` は、モデルパラメータのリストとその値を NamedTuple として返します。`unicode` が `false` に設定されている場合、ユニコード記号はそのテキストの同等物に変換されます。

# 例

```@example
julia> model = RheoModel(Maxwell, k=1, η=2.)
[...]

julia> getparams(m)
(k = 1.0, η = 2.0)

julia> getparams(m,unicode=false)
(k = 1.0, eta = 2.0)
```
