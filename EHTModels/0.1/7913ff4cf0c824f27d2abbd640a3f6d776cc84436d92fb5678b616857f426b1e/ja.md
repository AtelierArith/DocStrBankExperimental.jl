```
components(m::AbstractModel)
```

複合モデルのモデルコンポーネントを返します。これは、構築したすべてのモデルを含むタプルを返します。

# 例

```julia-repl
julia> m = Gaussian() + Disk()
julia> components(m)
(Gaussian{Float64}(), Disk{Float64}())
```
