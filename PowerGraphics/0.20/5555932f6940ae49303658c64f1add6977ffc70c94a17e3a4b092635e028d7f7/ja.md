```
save_plot(plot, filename)
```

指定されたファイル名にプロットを保存します

# 引数

  * `plot`: プロットオブジェクト
  * `filename::String` : ファイル名に保存

# 例

```julia
res = solve_op_problem!(OpProblem)
plot = plot_fuel(res)
save_plot(plot, "my_plot.png")
```

# 受け入れられるキーワード（現在は[PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl))バックエンドのみに実装されています）

  * `width::Union{Nothing,Int}=nothing`
  * `height::Union{Nothing,Int}=nothing`
  * `scale::Union{Nothing,Real}=nothing`
