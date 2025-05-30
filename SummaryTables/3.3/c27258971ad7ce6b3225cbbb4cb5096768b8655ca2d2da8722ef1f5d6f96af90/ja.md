```
function Table(cells;
    header = nothing,
    footer = nothing,
    round_digits = 3,
    round_mode = :auto,
    trailing_zeros = false,
    footnotes = [],
    postprocess = [],
    rowgaps = Pair{Int,Float64}[],
    colgaps = Pair{Int,Float64}[],
    linebreak_footnotes = true,
)
```

複数の形式（HTMLやLaTeXなど）でレンダリングできる`Table`を作成します。

## 引数

  * `cells::AbstractMatrix{<:Cell}`: テーブルを構成する`Cell`の行列。

## キーワード引数

  * `header`: ヘッダーの最後の行のインデックス。ヘッダーが指定されていない場合は`nothing`。
  * `footer`: フッターの最初の行のインデックス。フッターが指定されていない場合は`nothing`。
  * `footnotes`: テーブル内の対応するラベルを持たない`Annotated`値から派生していないフットノートとして印刷されるオブジェクトのベクター。
  * `round_digits = 3`: 浮動小数点値は印刷前にこの精度に丸められます。
  * `round_mode = :auto`: 浮動小数点値がどのように丸められるか。オプションは`:auto`、`:digits`または`:sigdigits`です。`round_mode === nothing`の場合、丸めは適用されず、`round_digits`と`trailing_zeros`は効果を持ちません。
  * `trailing_zeros = false`: 浮動小数点値が末尾のゼロを保持するかどうかを制御します。例えば、`4.0`と`4`の違い。
  * `postprocess = []`: テーブルを表示する前に左から右に適用されるポストプロセッサのリスト。ポストプロセッサは、要素単位で動作するか、テーブルオブジェクト全体に対して動作することができます。カスタムポストプロセッサを定義するための`postprocess_table`および`postprocess_cell`関数を参照してください。
  * `rowgaps = Pair{Int,Float64}[]`: ペア`index => gap_pt`のリスト。各ペアについて、行`index`と`index+1`の間に`gap_pt`のサイズの視覚的ギャップが追加されます。
  * `colgaps = Pair{Int,Float64}[]`: ペア`index => gap_pt`のリスト。各ペアについて、列`index`と`index+1`の間に`gap_pt`のサイズの視覚的ギャップが追加されます。
  * `linebreak_footnotes = true`: `true`の場合、各フットノートと注釈は別の行で始まります。

## 丸めモード

数値`0.006789`、`23.4567`、`456.789`または`12345.0`を考えます。

これらの数値が異なる利用可能な丸めモードでどのようにフォーマットされるかは次のとおりです。

  * `:auto`は`n`の有効桁数に丸めますが、`:sigdigits`とは異なり、カンマの前の追加の桁をゼロにしません。例えば、`round_digits = 3`は`0.00679`、`23.5`、`457.0`または`12345.0`になります。桁数が>= 6または<= -5の数値は、Juliaのように指数表記で表示されます。
  * `:digits`はカンマの後の`n`桁に丸め、複数の末尾のゼロを表示する可能性があります。例えば、`round_digits = 3`は`0.007`、`23.457`または`456.789`または`12345.000`になります。数値は決して指数表記で表示されません。
  * `:sigdigits`は`n`の有効桁数に丸め、`:auto`とは異なり、カンマの前の追加の桁をゼロにします。例えば、`round_digits = 3`は`0.00679`、`23.5`、`457.0`または`12300.0`になります。桁数が>= 6または<= -5の数値は、Juliaのように指数表記で表示されます。

```
