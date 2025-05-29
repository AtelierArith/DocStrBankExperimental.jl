```
function sup_ess(
    weights::AbstractMatrix{T},
    r_eff::AbstractVector{T}
) -> AbstractVector
```

PSISサンプルの上限に基づく有効サンプルサイズを計算します。すなわち、最大重みの逆数です。この指標は、`psis_ess`の`ess`よりも敏感ですが、はるかに変動が大きいです。L-∞ノルムを使用します。

# 引数

  * `weights`: PSISから導出された重要度サンプリング重みのセット。
  * `r_eff`: MCMCチェーンの相対効率; [`relative_eff`]@refも参照してください。
