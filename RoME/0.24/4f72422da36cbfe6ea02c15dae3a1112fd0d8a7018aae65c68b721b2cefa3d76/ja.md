```julia
duplicateToStandardFactorVariable(
    ,
    mpp,
    dfg,
    prevsym,
    newsym;
    solvable,
    graphinit,
    cov
)

```

特別な因子変数から標準因子および変数に値を複製するためのヘルパー関数。新しい因子の名前を返します。

ノート：

  * `MutablePosePose` でオドメトリを蓄積し、その後標準の PosePose と新しい変数をクローンするために開発されました。
  * 元の MutablePosePose ソース因子または変数をいかなる方法でも変更しません。
  * mpp オブジェクトからのタイムスタンプを前提としています。

関連

[`addVariable!`](@ref), [`addFactor!`](@ref)
