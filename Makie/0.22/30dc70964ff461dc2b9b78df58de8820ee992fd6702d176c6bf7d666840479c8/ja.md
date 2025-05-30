```
WilkinsonTicks(
    k_ideal::Int;
    k_min = 2, k_max = 10,
    Q = [(1.0, 1.0), (5.0, 0.9), (2.0, 0.7), (2.5, 0.5), (3.0, 0.2)],
    granularity_weight = 1/4,
    simplicity_weight = 1/6,
    coverage_weight = 1/3,
    niceness_weight = 1/4
)
```

`WilkinsonTicks`は`PlotUtils.optimize_ticks`の薄いラッパーであり、そのドキュメントは以下に再現されています：

optimize*ticks(xmin, xmax; extend*ticks::Bool = false,                Q = [(1.0,1.0), (5.0, 0.9), (2.0, 0.7), (2.5, 0.5), (3.0, 0.2)],                k*min = 2, k*max = 10, k*ideal = 5,                granularity*weight = 1/4, simplicity*weight = 1/6,                coverage*weight = 1/3, niceness*weight = 1/4,                strict*span = true, span_buffer = nothing)

目盛りの値を見つけます。

これは基本的に、データの周りのタイトなフィット、最適な目盛りの数、シンプルな数をバランスさせようとするウィルキンソンのアドホックスコアリングメソッドです。

## 引数：

  * `xmax`:

    データに現れる最大値。
  * `xmin`:

    データに現れる最小値。
  * `extend_ticks`:

    目盛り計算を拡張するかどうかを決定します。デフォルトはfalseです。
  * `strict_span`:

    [x*min, x*max]の外に目盛りが出ない場合はtrueです。デフォルトはtrueです。
  * `Q`:

    ラベリングがサンプリングされる素敵な数の分布。形式は(number, score)です。
  * `k_min`:

    最小目盛りの数。
  * `k_max`:

    最大目盛りの数。
  * `k_ideal`:

    理想的な目盛りの数。
  * `granularity_weight`:

    要求されたラベルの数に近い数を返すことを奨励します。
  * `simplicity_weight`:

    Qの中で早く現れるステップサイズを好むことによって、より素敵なラベリングシーケンスを奨励します。また、シーケンスを基礎付ける方法として0を含むラベリングを報酬します。
  * `coverage_weight`:

    データの範囲を大きく超えないラベリングを奨励し、不必要なホワイトスペースにペナルティを課します。
  * `niceness_weight`:

    素敵な範囲を生成するラベリングを奨励します。

## 戻り値：

`(ticklocations::Vector{Float64}, x_min, x_max)`

## 数学的詳細

ウィルキンソンの最適化関数は、3つのコンポーネントの合計として定義されます。ユーザーがmラベルを要求し、可能なラベリングがkラベルを持つ場合、コンポーネントは`simplicity`、`coverage`、`granularity`です。

これらのコンポーネントは次のように定義されます：

:$

\begin{aligned}   &\text{simplicity} = 1 - \frac{i}{|Q|} + \frac{v}{|Q|}
  &\text{coverage}   = \frac{x*{max} - x*{min}}{\mathrm{label}*{max} - \mathrm{label}*{min}}
  &\text{granularity}= 1 - \frac{\left|k - m\right|}{m} \end{aligned} :$

ここでの変数は：

  * `q`: `Q`の要素。
  * `i`: `q`のインデックス ∈ `Q`。
  * `v`: ラベル範囲に0が含まれる場合は1、そうでない場合は0。
