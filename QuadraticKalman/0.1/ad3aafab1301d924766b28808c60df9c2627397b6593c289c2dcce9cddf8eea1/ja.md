```
Moments{T<:Real}
```

二次カルマンフィルタの無条件モーメント構造。

この構造は、状態と拡張状態の長期（定常）モーメントをカプセル化します。これらのモーメントには、フィルタの初期化やモデルの動態の診断評価を行うために重要な平均と共分散の推定が含まれます。

フィールド：

  * state_mean::AbstractVector{T}: 状態の無条件（定常）平均ベクトル。
  * state_cov::AbstractMatrix{T}: 状態の無条件共分散行列。
  * aug_mean::AbstractVector{T}: 拡張状態の無条件平均ベクトル。
  * aug_cov::AbstractMatrix{T}: 拡張状態の無条件共分散行列。
