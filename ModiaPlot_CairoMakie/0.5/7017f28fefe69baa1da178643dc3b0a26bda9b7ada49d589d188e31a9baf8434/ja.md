```
plot(result, names; 
     heading = "", grid = true, xAxis = nothing,
     figure = 1, prefix = "", reuse = false, maxLegend = 10,
     minXaxisTickLabels = false,
     MonteCarloAsArea = true)
```

`result`データ構造の信号の**線グラフ**を、`ModiaResult.@usePlotPackage(xxx`で定義されたプロットパッケージを使用して、`names`キーで識別されたものを生成します。`xxx`の可能な値: `"GLMakie", "WGLMakie", "CairoMakie", "PyPlot", "NoPlot", "SilentNoPlot"`。

`result`は、`ModiaResult`の抽象インターフェースをサポートする任意のデータ構造です。現在、これらが含まれます：

  * `result::ModiaResult.ResultDict`
  * `result::AbstractDict{String,T}`
  * `result::DataFrames.DataFrame`
  * `result`は、`Tables.jl`インターフェースをサポートし、`Tables.columnaccess(result) = true`です。

引数`names`は、描画される図と、それぞれの図に含まれる結果データを定義します：

  * `names`が**String**の場合、キー`names`を持つ変数の1つの時系列を持つ1つの図を生成します。
  * `names`が**Tuple**のStringsの場合、タプルで指定されたキーを持つ変数の時系列を持つ1つの図を生成します。
  * `names`が**Vector**または**Matrix**の**Strings**および/または**Tuples**の場合、図のベクトルまたは行列を生成します。

注意、名前（および結果に利用可能な場合はその単位）は、自動的にそれぞれの図の凡例として使用されます。

`String`キーで識別される信号変数は、型`<:Number`のスカラーまたは型`<:Number`の配列である可能性があります。信号は、時間値のベクトル、対応する信号値のベクトル、および信号タイプ（連続またはクロック）によって定義されます。

注意、データをプロットパッケージに渡す前に、Float64に変換されます。これにより、たとえば、プロットパッケージがサポートしていなくても、有理数をプロットすることができます。`Measurements.Measurement{xxx}`および`MonteCarloMeasurements`は特別に処理されます。

# オプション引数

  * `heading::AbstractString`: 図の上に表示されるオプションの見出し。
  * `grid::Bool`: = true、グリッドを表示します。
  * `xAxis::Union{AbstractString,Nothing}`: x軸の名前。`xAxis=nothing`の場合、結果の独立変数（通常は`"time"`がx軸として使用されます）。
  * `figure::Int`: 図が描画されるウィンドウの整数識別子。
  * `prefix::AbstractString`: すべての凡例ラベルの前に追加される文字列（特に`reuse=true`の場合に便利）。
  * `reuse::Bool`: 図がすでに存在し、`reuse=false`の場合、プロットを追加する前に図をクリアします。そうでない場合、図に存在する曲線を削除せずに既存の図にプロットを含めます。`reuse = true`は`"WGLMakie"`には無視されます（サポートされていないため）。
  * `maxLegend::Int`: 1つのプロットコマンドの凡例エントリの数が`> maxLegend`の場合、凡例は抑制されます。すべての曲線は依然として名前をラベルとして持っています。PyPlotでは、ツールバーのボタン`Edit axis, curve ..`をクリックし、その後`Curves`をクリックすることで、曲線の名前を確認できます。
  * `minXaxisTickLabels::Bool`: = true、ベクトルまたは配列のプロットでx軸の目盛りラベルを削除する場合、最後の行を除きます（ドキュメントにプロットを含めるときに便利）。= false、x軸の目盛りラベルは常に表示されます（プロットにインタラクティブにズームインするときに便利）。
  * `MonteCarloAsArea::Bool`: = true、MonteCarloMeasurementsの値がすべての粒子の最小値と最大値の間の面積と平均値で表示される場合。= false、MonteCarloMeasurementsのすべての粒子の値が表示されます（たとえば、値に2000粒子がある場合、図には2000曲線が表示されます）。

# 例

```julia
import ModiaResult
using  Unitful

# "xxx"の"using"ステートメントを生成
# （"xxx"は以前のModiaResult.usePlotPackage("xxx")から）
ModiaResult.@usingModiaPlot

# 結果データを構築
t = range(0.0, stop=10.0, length=100);
result = Dict{String,Any}();
result["time"] = t*u"s";
result["phi"]  = sin.(t)*u"rad";
result["w"]    = cos.(t)*u"rad/s";
result["a"]    = 1.2*sin.(t)*u"rad/s^2";
result["r"]    = hcat(0.4 * cos.(t), 0.5 * sin.(t), 0.3*cos.(t))*u"m";

# 1つの図に1つの信号（凡例 = "phi [rad]"）
plot(result, "phi")

# 1つの図に3つの信号
plot(result, ("phi", "w", "a"), figure=2)

# 1つの信号を持つ図のベクトルとして3つの図
plot(result, ["phi", "w", "r"], figure=3)

# 1つの信号を持つ図の行列として4つの図
plot(result, ["phi" "w";
              "a"   "r[2]" ], figure=4)

# ベクトルとして2つの図
plot(result, [ ("phi", "w"), ("a") ], figure=5)

# 行列として4つの図
plot(result, [ ("phi",)           ("phi", "w");
               ("phi", "w", "a")  ("r[2:3]",)     ],figure=6)

# 1つの図にw=f(phi)をプロット
plot(result, "w", xAxis="phi", figure=7)

# 次のシミュレーション実行の信号をfigure=1に追加
# （凡例 = "Sim 2: phi [rad]"）
result["phi"] = 0.5*result["phi"];
plot(result, "phi", prefix="Sim 2: ", reuse=true)
```

プロットの行列の例：

![Matrix of plots](../resources/images/matrix-of-plots.png)
