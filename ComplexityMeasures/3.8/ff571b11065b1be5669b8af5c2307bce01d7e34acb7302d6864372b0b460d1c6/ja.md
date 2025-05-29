```
BubbleSortSwaps <: CountBasedOutcomeSpace
BubbleSortSwaps(; m = 3, τ = 1)
```

`BubbleSortSwaps` の結果空間は、[Manis2017](@citet) の「バブルエントロピー」に関する論文に基づいています。

## 説明

`BubbleSortSwaps` は以下のことを行います：

  * 入力データを埋め込み次元 `m` と埋め込みラグ `τ` を使用して埋め込みます
  * 埋め込み内の各状態ベクトルについて、バブルソートアルゴリズムが状態ベクトルをソートするために必要なスワップの数をカウントします。

[`counts_and_outcomes`](@ref) に対して、必要なスワップの数に関する分布を定義します。この分布は、[`probabilities_and_outcomes`](@ref) を使用して確率を推定するために使用でき、再び任意の [`InformationMeasure`](@ref) を推定するために使用できます。「シャノンバブルエントロピー」を計算する方法の例は以下に示されています。

## 結果空間

`BubbleSortSwaps` の [`outcome_space`](@ref) は整数 `0:N` であり、ここで `N = (m * (m - 1)) / 2 + 1` （最悪の場合のスワップ数）です。したがって、[`total_outcomes`](@ref) の数は `N + 1` です。

## 実装

  * [`codify`](@ref)。各埋め込まれた状態ベクトルに必要なスワップの数を返します。

## 例

`BubbleSortSwaps` の結果空間を使用すると、[Manis2017](@cite) に触発された「バブルエントロピー」を簡単に計算できます。注意：これは実際には新しいエントロピーではなく、入力データを離散化する新しい方法です。[Manis2017](@cite) からバブルエントロピーの複雑さ測定を再現するには、[`BubbleEntropy`](@ref) を参照してください。

## 例

```julia
using ComplexityMeasures
x = rand(100000)
o = BubbleSortSwaps(; m = 5) # 5次元の埋め込みベクトル
information(Shannon(; base = 2), o, x)

# 任意の確率推定器を使用して、他の「バブル量」、例えば 
# 「ツァリスバブルエクストロピー」を計算することもできます：
information(TsallisExtropy(), BayesianRegularization(), o, x)
```
