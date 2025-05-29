```
viz_response(data, 
             title="", xlabel="時間, t", 
             ylabel="出力, y*(t)",
             savename=nothing)
```

`data[:, :output]` と `data[:, :t]` をプロットして、入力に対するシステムの応答を視覚化します。通常、データフレーム `data` は [`simulate`](@ref) から返されます。

# 引数

  * `data::DataFrame`: 時系列データのデータフレームで、時間のための `:t` 列と出力のための `:output` 列を含みます。
  * `title::String`: プロットのタイトル
  * `xlabel::String`: xラベル
  * `ylabel::String`: yラベル
  * `savename::Union{Nothing, String}`: .png 形式の図として保存するためのファイル名。

# 戻り値

`CairoMakie.jl` の `Figure` オブジェクト。これは Pluto.jl ノートブックに表示されます。

`CairoMakie.jl` コマンドは、例えば以下のように `viz_response` の後に呼び出して、図のパネルにさらなる変更を加えることができます：

```julia
fig = viz_response(data)
ax = current_axis(fig)
ax.xlabel = "新しい xラベル"
xlims!(ax, 0, 15)
```

# 例

```
g = 4 / (4 * s ^ 2 + 0.8 * s + 1)
U = 1 / s
Y = g * U
data = simulate(Y, 50.0)
fig = viz_response(data)
```
