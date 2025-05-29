```
plot_demand!(plot, result)
plot_demand!(plot, system)
```

システムの需要をプロットします。

# 引数

  * `plot`: 既存のプロットハンドル、例えば [`plot()`](@extref RecipesBase.plot) の結果
  * `res::Union{`[`InfrastructureSystems.Results`](@extref)`,`[`PowerSystems.System`](@extref)`}`:    需要をプロットするための `Results` オブジェクト（例: [`PowerSimulations.SimulationProblemResults`](@extref)）または [`PowerSystems.System`](@extref)

# 受け入れられるキーワード

  * `linestyle::Symbol = :dash` : 線のスタイルを設定
  * `title::String`: プロットのタイトルを設定
  * `horizon::Int64`: 完全な結果よりも短い時間のウィンドウをプロットするため
  * `initial_time::DateTime`: 結果の初期時間とは異なる時間でプロットを開始するため
  * `aggregate::String = "System", "PowerLoad", or "Bus"`: 需要を [`PowerSystems.System`](@extref)、[`PowerSystems.PowerLoad`](@extref)、または [`PowerSystems.Bus`](@extref) によって集約し、発電機によってではなく
  * `set_display::Bool = true`: プロットの表示を防ぐために false に設定
  * `save::String = "file_path"`: プロットを保存するためのファイルパスを設定
  * `format::String = "png"`: [PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl)) プロットを保存するための異なるフォーマットを設定。オプションには "png"、"pdf"、"eps" が含まれます
  * `seriescolor::Array`: プロットの異なる色を設定
  * `title::String = "Title"`: プロットのタイトルを設定
  * `stack::Bool = true`: プロットトレースをスタック
  * `bar::Bool` : バープロットを作成
  * `nofill::Bool` : 空の領域の塗りつぶしを強制
  * `stair::Bool`: スタックプロットの代わりに階段プロットを作成
  * `filter_func::Function =`[`PowerSystems.get_available`](@extref PowerSystems.get_available-Tuple{Component}): プロットに含まれるコンポーネントをフィルタリング
  * `palette` : [`load_palette`](@ref) からのカラーパレット
