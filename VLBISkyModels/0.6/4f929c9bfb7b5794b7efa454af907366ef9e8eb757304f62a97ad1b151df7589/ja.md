```
components(m::AbstractModel)
```

複合モデルのモデルコンポーネントを返します。これは、構築したすべてのモデルを含むタプルを返します。

# 例

```julia-repl
julia> components(m)
m = Gaussian() + Disk()
```
