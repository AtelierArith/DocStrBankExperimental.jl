```
PlotDataMarker()
```

---

# 例

---

```
julia> marker = PlotDataMarker(
  size = [20, 30, 15, 10],
  color = [10.0, 20.0, 40.0, 50.0],
  cmin = 0.0,
  cmax = 50.0,
  colorscale = "Greens",
  colorbar = ColorBar(title_text = "Some rate", ticksuffix = "%", showticksuffix = "last"),
  line = PlotlyLine(color = "black")
)
```

---

# プロパティ

---

  * `autocolorscale::Bool` - colorscaleがデフォルトのパレット（`autocolorscale: true`）であるか、`marker.colorscale`によって決定されるパレットであるかを決定します。`marker.color`が数値配列に設定されている場合にのみ効果があります。`colorscale`が指定されていない場合や`autocolorscale`がtrueの場合、`color`配列内の数値がすべて正、すべて負、または混合されているかに応じてデフォルトのパレットが選択されます。デフォルト: `true`
  * `cauto::Bool` - 色のドメインが入力データ（ここでは`marker.color`）に基づいて計算されるか、`marker.cmin`および`marker.cmax`に設定された境界に基づいて計算されるかを決定します。`marker.color`が数値配列に設定されている場合にのみ効果があります。ユーザーによって`marker.cmin`および`marker.cmax`が設定されている場合はデフォルトで`false`になります。
  * `cmax::Float64,Nothing` - 色のドメインの上限を設定します。`marker.color`が数値配列に設定されている場合にのみ効果があります。値は`marker.color`と同じ単位である必要があり、設定されている場合は`marker.cmin`も設定されている必要があります。
  * `cmin::Float64` - `marker.cmin`および/または`marker.cmax`をこの点に等距離になるようにスケーリングすることによって、色のドメインの中点を設定します。`marker.color`が数値配列に設定されている場合にのみ効果があります。値は`marker.color`と同じ単位である必要があります。`marker.cauto`が`false`の場合は効果がありません。
  * `color::Union{String,Vector{Float64}}` - マーカーの色を設定します。特定の色または、配列の最大値と最小値に対して色スケールにマッピングされる数値の配列のいずれかを受け入れます。
  * `coloraxis::String` - 共有の色軸への参照を設定します。これらの共有色軸への参照は「coloraxis」、「coloraxis2」、「coloraxis3」などです。これらの共有色軸の設定は、レイアウトの`layout.coloraxis`、`layout.coloraxis2`などで設定されます。複数の色スケールが同じ色軸にリンクされることに注意してください。
  * `colorbar::ColorBar` - ColorBarオブジェクトは複数のキーを含みます。各キーの対応するAPIドキュメントを確認してください。例: `ColorBar(title_text = "Some rate", ticksuffix = "%", showticksuffix = "last")`
  * `colorscale::Union{Matrix,String}` - colorscaleを設定します。`marker.color`が数値配列に設定されている場合にのみ効果があります。colorscaleは、正規化された値をrgb、rgba、hex、hsl、hsv、または名前付きの色文字列にマッピングする配列を含む必要があります。最低でも、最小（0）および最大（1）値のマッピングが必要です。例えば、`[[0, 'rgb(0,0,255)'], [1, 'rgb(255,0,0)']]`。色空間内のcolorscaleの境界を制御するには、`marker.cmin`および`marker.cmax`を使用します。あるいは、`colorscale`は次のリストのパレット名の文字列である場合があります: Blackbody,Bluered,Blues,Cividis,Earth,Electric,Greens,Greys,Hot,Jet,Picnic,Portland,Rainbow,RdBu,Reds,Viridis,YlGnBu,YlOrRd.
  * `line::PlotlyLine` - オブジェクトは複数のキーを含みます。各キーの対応するAPIドキュメントを確認してください。例: `PlotlyLine(color = "black", width = 2)`
  * `opacity::Union{Float64, Vector{Float64}}` - マーカーの不透明度を設定します。タイプ。0と1の間または等しい数値または数値の配列
  * `reversescale::Bool` - trueの場合、色のマッピングを反転させます。`marker.color`が数値配列に設定されている場合にのみ効果があります。trueの場合、`marker.cmin`は配列の最後の色に対応し、`marker.cmax`は最初の色に対応します。
  * `showscale::Bool` - このトレースのために色バーが表示されるかどうかを決定します。`marker.color`が数値配列に設定されている場合にのみ効果があります。
  * `size::Union{Int,Vector{Int}}` - マーカーのサイズ（px単位）を設定します。
  * `sizemin::Float64` - `marker.size`が数値配列に設定されている場合にのみ効果があります。レンダリングされたマーカーポイントの最小サイズ（px単位）を設定します。
  * `sizemode::String` - `marker.size`が数値配列に設定されている場合にのみ効果があります。`size`内のデータがピクセルに変換されるルールを設定します。
  * `sizeref::Float64` - `marker.size`が数値配列に設定されている場合にのみ効果があります。マーカーポイントのレンダリングサイズを決定するために使用されるスケールファクターを設定します。`sizemin`および`sizemode`と一緒に使用します。
  * `symbol::Union{String, Vector{String}}` - マーカーのシンボルタイプを設定します。100を追加することは、シンボル名に「-open」を追加することと同等です。200を追加することは、シンボル名に「-dot」を追加することと同等です。300を追加することは、シンボル名に「-open-dot」または「dot-open」を追加することと同等です。例: デフォルト: "circle"
