```julia
bifurcationdiagram(
    prob,
    alg,
    level,
    options;
    linear_algo,
    kwargs...
)

```

問題 `F(x, p) = 0` に関連する分岐図を再帰的に計算します。

# 引数

  * `prob::AbstractBifurcationProblem` 分岐問題
  * `alg` 継続アルゴリズム
  * `level` 分岐図を計算するための最大分岐（または再帰）レベル
  * `options = (x, p, level) -> contparams` この関数は、分岐 `level` に応じて [`continuation`](@ref) オプションを変更することを可能にします。引数 `x, p` は `F(x, p)=0` に対する現在の解を示します。
  * `kwargs` オプションの引数。詳細については [`bifurcationdiagram!`](@ref) を参照してください。

# 簡略化された呼び出し:

次のメソッドも提供しています。

`bifurcationdiagram(prob, br::ContResult, level::Int, options; kwargs...)`

ここで `br` は、再帰的に分岐を計算したい [`continuation`](@ref) の呼び出し後に計算されたブランチです。
