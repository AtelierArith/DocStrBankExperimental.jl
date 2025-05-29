```
levene(observations::Array{Union{Number, Vector{Number}}})
levene(observations::Vector{Number}, factorassignments::Vector{Vector{Any}})
levene(df::DataFrame, observationscolumn::Symbol, factorcolumns::Vector{Symbol})
```

Leveneの等分散性検定を実行します。

少なくとも3つの交差因子（固定またはランダム）と、バランスの取れたデータ上の任意の数のランダムネスト因子で動作します。Leveneの検定は、各セルの絶対偏差に対してANOVAを実行することと同じです。

Leveneの検定が有意であれば、データは異方分散（分散が異なる）です。そうでない場合、分散が異なる可能性があるか、サンプルサイズが小さすぎて判断できない可能性があります。

# 引数

  * `observations`: テストする値を含む配列。配列の場合、各次元は因子レベルであり、observations[2,5,3]は最初の因子の2番目のレベル、2番目の因子の5番目のレベル、3番目の因子の3番目のレベルを示します。値または値のベクトルを含むことができ、ベクトルには複製が含まれます。因子は最も重要度の低いものから順に並べる必要があります。ベクトルの場合、因子レベルを指定するために`factorassignments`を提供する必要があります。
  * `factorassignments`: 各観測値がどの因子レベルに割り当てられるかを指定する整数のベクトルのベクトル。`observations`がベクトルとして与えられる場合にこれを提供します。因子レベルは連続している必要はなく、順序も必要ありません。ネストされた因子は、現在の因子レベルを再利用する必要があります。

注意: 複製がないことがわかる場合は例外をスローします。`hasrepliates=false`を使用して`anova()`に渡すデータ構造では使用しないでください。

出力: 各因子の検定結果を含む`AnovaData`構造体。

# 例

```julia
levene(observations)
```
