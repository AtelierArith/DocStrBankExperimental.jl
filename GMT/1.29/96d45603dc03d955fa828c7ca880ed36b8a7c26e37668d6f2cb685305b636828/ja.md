```
filter1d(cmd0::String="", arg1=nothing, kwargs...)
```

1次元データテーブルの時間領域フィルタリング。

## パラメータ

  * **F** | **filter** :: [Type => Str]   `Arg = type width[modifiers]`

    フィルタタイプを設定します。畳み込みフィルタと非畳み込みフィルタの中から選択します。フィルタコードの後に、時間列と同じ単位でフィルタ幅を追加します。
  * **D** | **inc** | **increment** :: [Type => Number]        `Arg = increment`

    $$
    increment
    $$

    は、系列が等間隔でサンプリングされていない場合に使用されます。この場合、インクリメントは横軸の解像度になります。
  * **E** | **end** | **ends** :: [Type => Bool | []]

    出力に時間系列の端を含めます。デフォルトでは、各端でデータのフィルタ幅の半分が失われます。
  * **L** | **gap_width** :: [Type => Number | Str]      `Arg = width`

    データの欠落条件をチェックします。入力データに幅を超えるギャップがある場合、そのポイントでは出力が得られません。
  * **N** | **time_col** | **timecol** :: [Type => Int]      `Arg = t_col`

    独立変数（時間）を含む列を示します。最も左の列は # 0、最も右の列は # (n_cols - 1) です。[デフォルトは 0 です]。
  * **Q** | **quality** :: [Type => Number]    `Arg = q_factor`

    畳み込みにおける平均重みをチェックすることで出力値の品質を評価します。q_factor を 0 と 1 の間で入力します。
  * **S** | **symmetry** :: [Type => Number]    `Arg = symmetry_factor`

    ウィンドウの中心に関するデータの対称性をチェックします。0 と 1 の間の因子を入力します。
  * **T** | **range** | **inc** :: [Type => List | Str]     `Arg = [min/max/]inc[+a|n]`

    min から max まで inc で均等に間隔を空けた時間ステップを作成します。[デフォルトは入力時間を使用します]。
  * `cumdist` | `cumsum`: [Type => Bool]

    入力ラインに沿った累積距離を計算します。このためには、最初の 2 列に空間座標が含まれている必要があります。

完全なドキュメントを見るには、次のように入力してください: $@? filter1d$
