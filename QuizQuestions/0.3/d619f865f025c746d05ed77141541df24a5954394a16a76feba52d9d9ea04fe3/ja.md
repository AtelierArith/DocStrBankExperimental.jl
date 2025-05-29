```
plotlylightq(p, xs=(-Inf, Inf), ys=(-Inf, Inf);
             label="", hint="", explanation="",
             correct_answer=nothing)
```

プロットの関数のPlotlyグラフから、ホバー時に表示されるグラフ上の `x-y` 点に関する質問を提示します。（複数のグラフがある図の場合、最初のグラフのホバーが取られます。パラメータ化されたプロットの場合、ホバーは予期しない方法で計算されることがあります。）

デフォルトでは、正しい答えは `xs` で指定された範囲内の `x` と `ys` で指定された範囲内の `y` の値を選択します。

  * `xs`: 選択された点の区間 `[x₀,x₁]` を指定し、デフォルトは `(-Inf,Inf)`
  * `ys`: 範囲 `[y₀,y₁]`
  * `correct_answer`: 指定された場合、より高度な正しさの概念を許可します。これは、クリック時にハイライトされるグラフ上のホバーされた点を表す `x` と `y` を持つJavaScriptコードスニペットです。

## 例

```
using PlotlyLight
xs = range(0, 2pi, length=100)
ys = sin.(xs)
p = Plot(Config(x=xs, y=ys))
plotlylightq(p, (3,Inf); label="``x>3``の値をクリックしてください")
```

デフォルトの採点スクリプトを修正する必要がある例です。また、`x`、`y` の値は *最初* のグラフを指します。（`correct answer` で定義を変更することができ、`x=e.points[0].x`、`y=e.points[0].y` を通じて見つけられます。）

```
xs = range(0, 2pi, length=100)
ys = sin.(xs)
p = Plot(Config(x=xs, y=ys));
push!(p.data, Config(x=xs, y=cos.(xs)));  # レイヤーを追加
question = "`sin(x)` が増加している値をクリックしてください"
# JavaScriptではpiがないためpi/2を評価し、またInfはInfinityに
correct_answer = "((x >= 0 && x <= 1.5707963267948966) || (x >= 4.71238898038469 && x <= 6.283185307179586))"
plotlylightq(p; label=question, correct_answer=correct_answer)
```

!!! note
    `PlotlyLight` グラフィックスの使用は `Weave` と `Pluto` で機能しますが、`quarto` と `Documenter` からは使用できません。

