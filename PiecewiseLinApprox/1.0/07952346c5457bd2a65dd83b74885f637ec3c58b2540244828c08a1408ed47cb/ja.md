```
Linearize(expr_fct::Ef,x1::Real,x2::Real, e::ErrorType; bounding = Best() ::BoundingType, ConcavityChanges = [Inf]::Array{Float64,1})
```

`x1` から `x2` までの `expr_fct` の最適な区分線形近似を作成します。結果は `LinearPiece` の配列になります。この配列は関数として直接呼び出すことができます。

# 引数

  * `expr_fct` : R から R への線形化する関数（式またはネイティブの Julia 関数のいずれか）
  * `x1` : 開始点
  * `x2` : 終了点
  * `e` : エラータイプ、Absolute() または Relative() のいずれか

# オプション引数

  * `bounding` : `Under()` は過小評価、`Over()` は過大評価、`Best()` は関数の下または上に行く評価を行います。デフォルトでは `Best()` が使用されます。
  * `ConcavityChanges` : 関数の凹凸の変化。指定しない場合は自動的に計算されますが、稀に凹凸がゼロに漸近する場合に精度エラーが発生することがあります。

!!! note
    `HeuristicLin()` と `ExactLin()` のどちらのアルゴリズムを使用するかをエラータイプの後に追加することで指定することも可能です。デフォルトでは PiecewiseLinApprox はヒューリスティックを使用します。


!!! note
    関数が式で与えられた場合、変数は `x` であると仮定されます。


# 例

```julia-repl
julia> pwl = Linearize(:(x^2),0,2,Absolute(0.1))
3-element Vector{PiecewiseLinApprox.LinearPiece}:
 0.894427190999916 x -0.1 from 0.0 to 0.894427190999916
 2.683281572999748 x -1.7000000000000006 from 0.894427190999916 to 1.7888543819998326
 4.736067977499794 x -5.372135954999589 from 1.7888543819998326 to 2.0

julia> pwl(1)
0.9832815729997475
```
