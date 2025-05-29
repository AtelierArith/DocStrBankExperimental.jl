```
plot_topoplotseries(f::Union{GridPosition, GridLayout, Figure}, data::Union{<:Observable{<:DataFrame},DataFrame}; kwargs...)
plot_topoplotseries!(data::Union{<:Observable{<:DataFrame},DataFrame}; kwargs...)
```

定期的な間隔での複数のミニチュアトポプロット。

## 引数

  * `f::Union{GridPosition, GridLayout, GridLayoutBase.GridSubposition, Figure}`   プロットを描画するための `Figure`、`GridLayout`、`GridPosition`、または `GridLayoutBase.GridSubposition`。
  * `data::Union{<:Observable{<:DataFrame},DataFrame}`   データを含むDataFrameまたはObservable DataFrame。   デフォルトでは `time` 列が必要ですが、`mapping=(; x=:my_column)` を指定することで任意の連続またはカテゴリカル列に上書きできます。

## キーワード引数 (kwargs)

  * `bin_width::Real = nothing`   連続x値のビンの幅をその単位で指定する数値。
  * `bin_num::Real = nothing`   トポプロットの数。   `bin_width` または `bin_num` のいずれかを指定する必要があります。両方を指定した場合はエラーになります。   `mapping.col` または `mapping.row` がカテゴリカルの場合、`bin_width` と `bin_num` は `nothing` のままです。
  * `combinefun::Function = mean`   `bin_width` 内のサンプルをどのように要約するかを指定します。   例の関数: `mean`、`median`、`std`。
  * `rasterize_heatmaps::Bool = true`   `svg` 形式で保存する際にプロットのヒートマップのラスタライズを強制します。   補間されたヒートマップを除き、すべての線/点はベクターです。   これは通常望ましいものであり、そうでない場合は各トポプロットに約128x128のベクターが生成され、すべてが非常に遅くなります。
  * `col_labels::Bool`, `row_labels::Bool = true`   ファセットモードで列と行のラベルを表示します。（未実装）
  * `positions::Vector{Point{2, Float32}} = nothing`   チャンネルの位置を指定します。すべてのユニークな電極のxおよびy位置のリストが必要です。
  * `labels::Vector{String} = nothing`   各電極のラベルを表示します。
  * `interactive_scatter = nothing`   インタラクティブモードを有効にします。   `obs_tuple = Observable((0, 0, 0))` を作成し、それを `interactive_scatter` に渡すと、クリックされたトポプロットマーカーのインデックスでオブザーバブルタプルを更新できます。   `(0, 0, 0)` は（トポプロットレイアウトの行、トポプロットレイアウトの列、電極）に対応します。
  * `topo_axis::NamedTuple = (;)`   ここでトポプロットの設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで `?Axis` と入力してください。
  * `mapping = (; col = :time`, row = nothing, layout = nothing)   `mapping.col` - x値を指定します。任意の連続またはカテゴリカル変数を使用できます。   `mapping.row` - y値を指定します。任意の連続またはカテゴリカル変数を使用できます（未実装）。   `mapping.layout` - `:time` と等しい場合にトポプロットを行で配置します。
  * `topo_attributes::NamedTuple = (;)`   ここでトポプロットの補間の設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで `?Topoplot.topoplot` と入力してください。   デフォルト: interp_resolution = (128, 128)、interpolation = CloughTocher()
  * `topolabels_rounding = (; sigdigits = 3)`   topo_axisラベルの丸め。   `sigdigits` - 有効数字の数。   `digits` - 小数点以下の桁数。   `sigdigits` または `digits` のいずれか一方のみを提供する必要があります。

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトがサイクルされて一致します。

`;` を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/) の `kwargs...` を使用してください* 

**axis =** (xlabel = "時間ウィンドウ", aspect = Makie.DataAspect(), title = "", titlesize = 16, titlefont = :bold, ylabel = "", ylabelpadding = 25, xlabelpadding = 25, xpanlock = true, ypanlock = true, xzoomlock = true, yzoomlock = true, xrectzoom = false, yrectzoom = false) - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/) の `kwargs...` を使用してください* 

**layout =** (show*legend = true, use*colorbar = true, hidespines = (), hidedecorations = Dict{Symbol, Bool}(:label => 0)) - *この [ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/) を確認してください* 

**mapping =** (x = nothing, y = (:estimate, :yhat, :y), positions = (:pos, :positions, :position, nothing), labels = (:labels, :label, :sensor, nothing), col = (:time,), row = (nothing,)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/) の任意のマッピングを使用してください* 

**visual =** (colormap = Makie.Reverse{Symbol}(:RdBu), contours = (color = :white, linewidth = 2), enlarge = 1, label*scatter = false, label*text = false, bounding*geometry = GeometryBasics.Circle, levels = nothing) - *[`Topoplot.eeg*topoplot`](https://makieorg.github.io/TopoPlots.jl/stable/eeg/) の`kwargs...` を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/) の `kwargs...` を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, flipaxis = true, label = "電圧 [µV]") - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/) の `kwargs...` を使用してください* 

**戻り値:** トポプロットシリーズを表示する `Figure`。
