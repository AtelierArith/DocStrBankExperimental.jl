```
plot_fuel(results)
```

燃料タイプごとの結果のスタックプロットを描画し、各燃料タイプに特定の色を割り当てます。

# 引数

  * `res::`[`InfrastructureSystems.Results`](@extref):    プロットするための`Results`オブジェクト（例：[`PowerSimulations.SimulationProblemResults`](@extref)）

    # 例

```julia
res = solve_op_problem!(OpProblem)
plot = plot_fuel(res)
```

# 受け入れられるキーワード

  * `generator_mapping_file` = "file_path" : 燃料とプライムムーバーによる発電機カテゴリを定義するyamlのファイルパス
  * `variables::Union{Nothing, Vector{Symbol}}` = nothing : プロットする特定の変数
  * `slacks::Bool = true` : スラック変数を表示
  * `load::Bool = true` : 負荷ラインを表示
  * `curtailment::Bool = true`: スタックプロットにおけるカーテイルメントをプロットする
  * `set_display::Bool = true`: プロットの表示を防ぐためにfalseに設定
  * `save::String = "file_path"`: プロットを保存するためのファイルパスを設定
  * `format::String = "png"`: [PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl))プロットを保存するための異なるフォーマットを設定。オプションには"png"、"pdf"、"eps"が含まれます
  * `seriescolor::Array`: プロットの異なる色を設定
  * `title::String = "Title"`: プロットのタイトルを設定
  * `stack::Bool = true`: プロットトレースをスタック
  * `bar::Bool` : バープロットを作成
  * `nofill::Bool` : 空の領域の塗りつぶしを強制
  * `stair::Bool`: スタックプロットの代わりに階段プロットを作成
  * `filter_func::Function =`[`PowerSystems.get_available`](@extref PowerSystems.get_available-Tuple{Component}): プロットに含まれるコンポーネントをフィルタリング
