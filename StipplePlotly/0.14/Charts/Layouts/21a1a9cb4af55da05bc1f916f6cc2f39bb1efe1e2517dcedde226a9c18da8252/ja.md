```
ColorBar()
```

---

# 例

---

```
julia> 
```

---

# プロパティ

---

  * `bgcolor::String` - パディングエリアの色を設定します。
  * `bordercolor::String` - 軸線の色を設定します。デフォルト = `"#444"`
  * `borderwidth::Int` - このカラーバーを囲む境界の幅（px単位）を設定します。デフォルト = `0`
  * `dtick::Union{Float64,Int,String}` - この軸の目盛り間のステップを設定します。`tick0`と一緒に使用します。正の数である必要があります。または、"log"および"date"軸に利用可能な特別な文字列です。軸の`type`が"log"の場合、目盛りは10^(n"dtick)ごとに設定されます。ここでnは目盛り番号です。たとえば、1、10、100、1000で目盛りを設定するには、`dtick`を1に設定します。1、100、10000で目盛りを設定するには、`dtick`を2に設定します。1、5、25、125、625、3125で目盛りを設定するには、`dtick`をlog_10(5)または0.69897000433に設定します。"log"にはいくつかの特別な値があります。"L<f>"の形式で、`f`は正の数で、値（ただし位置ではない）で線形に間隔を置いた目盛りを提供します。たとえば、`tick0` = 0.1、`dtick` = "L0.5"は、目盛りを0.1、0.6、1.1、1.6などに配置します。10の累乗とその間の小さな数字を表示するには、"D1"（すべての数字）または"D2"（2と5のみ）を使用します。`tick0`は"D1"および"D2"の場合は無視されます。軸の`type`が"date"の場合、時間をミリ秒に変換する必要があります。たとえば、目盛り間の間隔を1日に設定するには、`dtick`を86400000.0に設定します。"date"にも特別な値があり、"M<n>"は月数で間隔を置いた目盛りを提供します。`n`は正の整数である必要があります。3ヶ月ごとの15日に目盛りを設定するには、`tick0`を"2000-01-15"に設定し、`dtick`を"M3"に設定します。4年ごとに目盛りを設定するには、`dtick`を"M48"に設定します。
  * `exponentformat::String` - 目盛りの指数のフォーマットルールを決定します。たとえば、数値1,000,000,000を考えます。"none"の場合、1,000,000,000として表示されます。"e"の場合、1e+9。"E"の場合、1E+9。"power"の場合、1x10^9（9は上付き文字）。"SI"の場合、1G。"B"の場合、1B。デフォルト - `"B"`
  * `len::Union{Float64,Int}` - カラーバーの長さを設定します。この測定値は両端のパディングを除外します。つまり、カラーバーの長さはこの長さから両端のパディングを引いたものです。
  * `lenmode::String` - カラーバーの長さがプロットの"fraction"単位で設定されるか、"pixels"単位で設定されるかを決定します。値を設定するには`len`を使用します。
  * `minexponent::Int` - |n|がこの数値未満の場合、10^nのSI接頭辞を非表示にします。これは`tickformat`が"SI"または"B"の場合にのみ影響があります。デフォルト - `0`
  * `nticks::Int` - 特定の軸の最大目盛り数を指定します。実際の目盛り数は自動的に`nticks`以下に選択されます。`tickmode`が"auto"に設定されている場合にのみ影響があります。デフォルト - `0`
  * `outlinecolor::String` - 軸線の色を設定します。
  * `outlinewidth::Int` - 軸線の幅（px単位）を設定します。
  * `separatethousands::Bool` - "true"の場合、4桁の整数も区切られます。
  * `showexponent::Bool` - "all"の場合、すべての指数がその有効数字の横に表示されます。"first"の場合、最初の目盛りの指数のみが表示されます。"last"の場合、最後の目盛りの指数のみが表示されます。"none"の場合、指数は表示されません。
  * `showticklabels::Bool` - 目盛りラベルが描画されるかどうかを決定します。
  * `showtickprefix::Bool` - "all"の場合、すべての目盛りラベルが接頭辞付きで表示されます。"first"の場合、最初の目盛りのみが接頭辞付きで表示されます。"last"の場合、最後の目盛りのみが接尾辞付きで表示されます。"none"の場合、目盛り接頭辞は非表示になります。
  * `showticksuffix::Bool` - `showtickprefix`と同様ですが、目盛り接尾辞に関してです。
  * `thickness::Int` - カラーバーの厚さを設定します。この測定値はパディング、目盛り、ラベルのサイズを除外します。
  * `thicknessmode::String` - カラーバーの厚さがプロットの"fraction"単位で設定されるか、"pixels"単位で設定されるかを決定します。値を設定するには`thickness`を使用します。
  * `tick0::Union{Float64,Int,String}` - この軸の最初の目盛りの配置を設定します。`dtick`と一緒に使用します。軸の`type`が"log"の場合、開始目盛りの対数を取る必要があります（たとえば、開始目盛りを100に設定するには、`tick0`を2に設定します）。ただし、`dtick`=*L<f>*の場合（詳細は`dtick`を参照）、軸はゼロから始まります。軸の`type`が"date"の場合、日付文字列である必要があります。軸の`type`が"category"の場合、各カテゴリが出現する順序でゼロからの連番が割り当てられるスケールを使用して数値である必要があります。
  * `tickangle::Union{String,Int,Float64}` - 水平に対する目盛りラベルの角度を設定します。たとえば、`tickangle`が-90の場合、目盛りラベルが垂直に描画されます。
  * `tickcolor::String` - 目盛りの色を設定します。
  * `tickformat::String` - d3フォーマットのミニ言語を使用して目盛りラベルのフォーマットルールを設定します。これらはPythonのものに非常に似ています。数値については、https://github.com/d3/d3-format/tree/v1.4.5#d3-formatを参照してください。日付については、https://github.com/d3/d3-time-format/tree/v2.2.3#locale_formatを参照してください。d3の日付フォーマッタに2つの項目を追加します："%h"は年の半分を小数として、"%{n}f"はn桁の小数秒です。たとえば、"2016-10-13 09:15:23.456"に対して、`tickformat`が"%H~%M~%S.%2f"の場合、"09~15~23.46"と表示されます。
  * `tickformatstops::Dict` - 各オブジェクトが1つ以上のキー - "dtickrange"、"value"、"enabled"、"name"、"templateitemname"を持つオブジェクトの配列。
  * `ticklabeloverflow::String` - グラフのdivまたは軸のドメインをオーバーフローする目盛りラベルをどのように処理するかを決定します。内部目盛りラベルのデフォルト値は"hide past domain"です。他の場合のデフォルトは"hide past div"です。
  * `ticklabelposition::String` - 目盛りラベルが目盛りに対してどこに描画されるかを決定します。`orientation`が"h"の場合は左と右のオプション、`orientation`が"v"の場合は上と下のオプションが使用されます。タイプ: 列挙型、( "outside" | "inside" | "outside top" | "inside top" | "outside left" | "inside left" | "outside right" | "inside right" | "outside bottom" | "inside bottom" )のいずれか。デフォルト: "outside"
  * `ticklabelstep::String` - 目盛り間の間隔に対する目盛りラベル間の間隔を設定します。1の値（デフォルト）は各目盛りにラベルが付くことを意味します。2の値は2番目のラベルを表示します。大きな値nは、n番目の目盛りのみがラベル付けされることを意味します。`tick0`は表示されるラベルを決定します。`type`が"log"または"multicategory"の場合、または`tickmode`が"array"の場合は実装されていません。
  * `ticklen::Int` - 目盛りの長さ（px単位）を設定します。タイプ: 0以上の数値 | デフォルト: 5
  * `tickmode::String` - この軸の目盛りモードを設定します。"auto"の場合、目盛りの数は`nticks`を介して設定されます。"linear"の場合、目盛りの配置は開始位置`tick0`と目盛りステップ`dtick`によって決定されます（`tick0`と`dtick`が提供されている場合、"linear"がデフォルト値です）。"array"の場合、目盛りの配置は`tickvals`を介して設定され、目盛りテキストは`ticktext`です（`tickvals`が提供されている場合、"array"がデフォルト値です）。タイプ: 列挙型、( "auto" | "linear" | "array" )のいずれか。デフォルト: "array"
  * `tickprefix::String` - 目盛りラベルの接頭辞を設定します。タイプ: 文字列 デフォルト: ""
  * `ticks::String` - 目盛りが描画されるかどうかを決定します。""の場合、この軸の目盛りは描画されません。"outside"（"inside"）の場合、この軸の目盛りは軸線の外側（内側）に描画されます。タイプ: 列挙型、( "outside" | "inside" | "" )のいずれか。デフォルト: ""
  * `ticksuffix::String` - 目盛りラベルの接尾辞を設定します。タイプ: 文字列 デフォルト: ""
  * `ticktext::Vector{String}` - `tickvals`を介して目盛り位置に表示されるテキストを設定します。`tickmode`が"array"に設定されている場合にのみ効果があります。`tickvals`と一緒に使用します。タイプ: 文字列のベクトル
  * `tickvals::Vector{Float64}` - この軸に目盛りが表示される値を設定します。`tickmode`が"array"に設定されている場合にのみ効果があります。タイプ: 数値のベクトル
  * `tickwidth::Int` - 目盛りの幅（px単位）を設定します。タイプ: 0以上の数値 | デフォルト: 1
  * `title_font::Font` - このカラーバーのタイトルフォントを設定します。
  * `title_side::String` - カラーバータイトルの位置をカラーバーに対して決定します。`orientation`が"v"の場合はデフォルトで"top"、`orientation`が"h"の場合はデフォルトで"right"です。
  * `title_text::String` - カラーバーのタイトルを設定します。
  * `x::Float64` - カラーバーのx位置を設定します（プロットの割合で）。`orientation`が"v"の場合はデフォルトで1.02、`orientation`が"h"の場合は0.5です。タイプ: -2から3の間の数値
  * `xanchor::String` - このカラーバーの水平位置のアンカーを設定します。このアンカーは、カラーバーの"x"位置を"left"、"center"、または"right"に結びつけます。`orientation`が"v"の場合はデフォルトで"left"、`orientation`が"h"の場合は"center"です。タイプ: 列挙型、( "auto" | "left" | "center" | "right" )のいずれか
  * `xpad::Int` - x方向のパディング量（px単位）を設定します。タイプ: 0以上の数値 | デフォルト: 0
  * `y::Float64` - カラーバーのy位置を設定します（プロットの割合で）。`orientation`が"v"の場合はデフォルトで0.98、`orientation`が"h"の場合は0.5です。タイプ: -2から3の間の数値
  * `yanchor::String` - このカラーバーの垂直位置のアンカーを設定します。このアンカーは、カラーバーの"y"位置を"top"、"middle"、または"bottom"に結びつけます。`orientation`が"v"の場合はデフォルトで"middle"、`orientation`が"h"の場合は"bottom"です。タイプ: 列挙型、("top" | "middle" | "bottom" )のいずれか
  * `ypad::Int` - y方向のパディング量（px単位）を設定します。タイプ: 0以上の数値 | デフォルト: 10
