```julia
(1)
function predictAcc(yTrue::IntVector, yPred::IntVector;
		scoring	:: Symbol = :b,
		digits	:: Int=3)

(2)
function predictAcc(CM::Union{Matrix{R}, Matrix{S}};
		scoring	:: Symbol = :b,
		digits	:: Int=3) where {R<:Real, S<:Int}
```

予測精度を比率として返します。すなわち、∈$[0, 1]$、次のいずれかが与えられます。

  * (1) 真のラベルの整数ベクトル `yTrue` と予測されたラベルの整数ベクトル `yPred`、または
  * (2) 混同行列。

混同行列は整数を保持する場合、*頻度*（カウント）を表すものとして解釈され、実数を保持する場合、*比率*を表すものとして解釈されます。

`scoring`=:b（デフォルト）の場合、**バランス精度**が計算されます。他の値を指定すると、関数は通常の**精度**を返します。バランス精度は不均衡なクラスに対して好まれます。均衡なクラスの場合、バランス精度は通常の精度に減少するため、クラスが均衡している場合に通常の精度を使用する意味はありません。

誤差はオプションのキーワード引数 `digits` の桁数に丸められ、デフォルトは3です。

**数学**

通常の*精度*は、*比率*を表す混同行列の対角要素の合計によって与えられます。

*バランス精度*の場合、混同行列の対角要素はそれぞれの行の合計で割られ、その平均が取られます。

**参照** [`predict`](@ref), [`predictErr`](@ref), [`confusionMat`](@ref)

**例**

```julia
using PosDefManifoldML
predictAcc([1, 1, 1, 2, 2], [1, 1, 1, 1, 2]; scoring=:a)
# 通常の精度、返り値: 0.8
predictAcc([1, 1, 1, 2, 2], [1, 1, 1, 1, 2])
# バランス精度、返り値: 0.75
```
