```
Kaczmarz(A; reg = L2Regularization(0), normalizeReg = NoNormalization(), randomized=false, subMatrixFraction=0.15, shuffleRows=false, seed=1234, iterations=10)
```

`A`のためのKaczmarzオブジェクトを作成します。

# 必要な引数

  * `A`                                                 - 前方演算子

# オプションのキーワード引数

  * `reg::AbstractParameterizedRegularization`          - 正則化項
  * `normalizeReg::AbstractRegularizationNormalization` - 正則化正規化スキーム; オプションは`NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `randomized::Bool`                                    - Kaczmarzアルゴリズムをランダム化
  * `subMatrixFraction::Real`                             - ランダム化Kaczmarzアルゴリズムで使用される行の割合
  * `shuffleRows::Bool`                                   - Kaczmarzアルゴリズムをランダム化
  * `seed::Int`                                           - ランダム化アルゴリズムのシード
  * `iterations::Int`                                     - イテレーションの数

さらに[`createLinearSolver`](@ref), [`solve!`](@ref)を参照してください。
