```
anova(observations::Array{Union{Number, Vector{Number}}}, factortypes = FactorType[]; factornames = String[], hasreplicates = true)
anova(observations::Vector{Number}, factorassignments::Vector{Vector{Any}}, factortypes = FactorType[]; factornames = String[], hasreplicates = true)
anova(df::DataFrame, observationscolumn::Symbol, factorcolumns::Vector{Symbol}, factortypes = FactorType[]; factornames = String[])
```

分散分析（ANOVA）計算を実行します。

固定またはランダム因子、被験者/ブロック因子、入れ子因子に対して、複製の有無にかかわらず、バランスの取れたデータで操作します。

制限事項：

  * いずれかの因子が `random` 型の場合、3要因に制限されます
  * 繰り返し測定ANOVA（被験者/ブロック因子を含む）は、被験者内または被験者間に分割できる3つの `fixed` 因子に制限されます

最大3つの交差因子（固定またはランダム）と、任意の数のランダム入れ子因子に対して、複製の有無にかかわらず、バランスの取れたデータで操作します。

# 引数

  * `observations`: テストする値を含む配列。配列の場合、各次元は因子レベルであり、observations[2,5,3]は最初の因子の2番目のレベル、2番目の因子の5番目のレベル、3番目の因子の3番目のレベルを示します。値または値のベクトルを含むことができ、ベクトルには複製が含まれます。因子は最も重要度の低いものから順に並べる必要があります。ベクトルの場合、因子レベルを指定するために `factorassignments` を提供する必要があります。
  * `factorassignments`: 各観測値が因子レベルにどのように割り当てられるかを指定する整数のベクトルのベクトル。`observations` がベクトルとして与えられる場合にこれを提供します。因子レベルは連続している必要はなく、順序も必要ありません。入れ子因子は現在の因子レベルを再利用する必要があります。
  * `factortypes`: 各因子の `FactorType` を示すベクトル。因子は `nested` が最初、その後に `random`/`measured` または `fixed`/`manipulated` のいずれかの順で並べる必要があります。繰り返し測定の場合、`subject` または `block` は被験者内の `fixed` の後、被験者間の `fixed` の前に出現する必要があります。提供される値が少なすぎる場合、残りは `fixed` と見なされます。
  * `factornames`: 複製因子を除く各因子の名前のベクトル。空の場合、自動的にアルファベット順に埋められます。
  * `hasreplicates`: 最初のレベルを考慮するかどうかを指定するブール値

注意：最後のインデックスはテーブルの最上位因子になります。

出力：各因子のテスト結果を含む `AnovaData` 構造。

# 例

```julia
anova(observations)                           # 複製ありのN要因固定効果ANOVA（ベクトルまたは最初の次元）
anova(observations, hasreplicates = false)    # 複製なしのN要因固定効果ANOVA（最初の次元）
anova(observations, [random])                 # 下位ランダム因子と1または2の上位固定因子を持つN要因ANOVA
anova(observations, [random])                 # 下位ランダム因子と1または2の上位固定因子を持つN要因ANOVA
anova(observations, [fixed, random])          # 1つの下位固定因子、1つのランダム因子、0または1の上位固定因子を持つN要因ANOVA
anova(observations, [nested, random])         # 1つのランダム入れ子因子、1つのランダム因子、1-2の固定因子を持つN要因固定効果ANOVA
anova(observations, [fixed, subject])         # 1つの被験者内固定因子を持つN要因繰り返し測定ANOVA
anova(observations, [fixed, block])           # 1つのブロック内固定因子を持つN要因繰り返し測定ANOVA
anova(observations, [nested, fixed, subject]) # 1つの被験者内固定因子と1つの入れ子因子を持つN要因繰り返し測定ANOVA
```

# 用語集

  * observation: 従属変数。
  * factor: 独立変数。
  * factor level: 因子の値。
  * balanced: 因子レベルのすべての組み合わせが同じ数の観測値を持つ。
  * crossed factor: 他のすべての交差因子のレベルと組み合わさるレベルを持つ因子。
  * fixed/manipulated factor: 固定効果を持つ因子（例：処置、濃度、曝露時間）。
  * random/measured factor: ランダム効果を持つ因子（例：場所、個体）。
  * nested factor: 交差因子レベルの組み合わせに固有のレベルを持つランダム因子（例：複製）。
  * subject/block factor: 別の因子の複数のレベルにさらされる入れ子因子。
  * sum of squares (SS): サンプルサイズに依存する分散の尺度。「平方和偏差」とも呼ばれます。
  * degrees of freedom (DF, ν): 値が移動できるビンの数、ランダムであれば。
  * mean square (MS): SS / DF。ランダム値がより多くのビンに割り当てられる場合に期待される大きな分散を修正します。「平均二乗誤差」または「平均二乗偏差」とも呼ばれます。
  * F-statistic: MS値の割り算は「F分布」に属する結果を生成し、その形状は分子と誤差のDFに依存します。この値の分布上の位置がp値を提供します。
  * p-value: すべての測定が同じ母集団から引き出された場合、観測値に含まれるデータと同じかそれ以上の極端なデータを得る確率。
  * effect size (ω²): 因子によって引き起こされる測定の標準化された差。これは、研究デザインに対して大きく安定した一般化されたバージョンです。
