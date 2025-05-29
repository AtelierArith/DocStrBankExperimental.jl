```
struct RegressionType{T}
    val::T
    is_iv::Bool
end
```

回帰のタイプ。`val` は [Distributions.jl](https://github.com/JuliaStats/Distributions.jl) パッケージからの分布である必要があります。`is_iv` は回帰が計量経済学的手法の回帰であるかどうかを示します。回帰タイプのデフォルトラベルは「Estimator」です。個々の回帰タイプ（例：「OLS」、「Poisson」）のラベルは、次のように実行することで設定できます：

```julia
RegressionTables.label_ols(render::AbstractRenderType) = $name
RegressionTables.label_iv(render::AbstractRenderType) = $name
```

または、個々の分布については、次のように実行することで設定できます：

```julia
Base.repr(render::AbstractRenderType, x::$Distribution; args...) = $Name
```
