```
theme_acs(; kwargs...)
```

ACS（アメリカ化学会）用の図を生成するためのMakieテーマを作成します。

図を保存するには、`savefig("path_to_figure.pdf", fig)`または`save("path_to_figure.pdf", fig, pt_per_unit=1.0)`を使用します。

# 引数

  * `width=3.25`: 図の幅（単位：インチ）。
  * `colors=COLORS[1]`: 色のリストで指定されたカラーパレット。
  * `linestyles=LINESTYLES`: サイクルされる線スタイルのリスト。
  * `markers=MARKERS`: サイクルされるマーカーのリスト。
  * `ishollowmarkers`: 現在のマーカーが空洞かどうかを示す`true`または`false`の値のリスト。
  * `palette=nothing`: Makieによって使用されるパレット。`nothing`でない場合は`NamedTuple`です。例：(color=COLORS[1], marker=MARKERS)。キーは`cycle`、`linecycle`、および`scattercycle`によって参照されます。
  * `cycle=CYCLE`: Makieが図のプロパティをどのようにサイクルするかを示すMakie `Cycle`インスタンス。
  * `linecycle=nothing`: `Line`プロットで使用される`Cycle`インスタンス。`nothing`の場合は、代わりに`cycle`の値が使用されます。
  * `scattercycle=nothing`: `Scatter`プロットで使用される`Cycle`インスタンス。`nothing`の場合は、代わりに`cycle`の値が使用されます。
  * `markerstrokewidth=0`: マーカーのストローク幅をカスタマイズします。
  * `heightwidthratio=HWRATIO`: 図のアスペクト比を`width`の倍数として設定します。
  * `usetexfont=true`: Makieが[`MathTexEngine.jl`](https://github.com/Kolaru/MathTeXEngine.jl)によって提供されるComputerModernフォントを使用するかどうかを設定します。

他にも[`theme_aps`](@ref)、[`theme_rsc`](@ref)、および[`theme_web`](@ref)を参照してください。
