```
qkf_smoother( Z, P, Z_pred, P_pred, T_bar, H_aug, G_aug, Φ_aug, dof ) -> (Z_smooth, P_smooth)
```

QKFスムーザーのアウトオブプレースバージョン。入力配列を上書きするのではなく、新しい配列を返します。

# 説明

qkf*smoother!と論理的には同じですが、スムーズな結果のために新しい配列Z*smoothとP_smoothを割り当てます。これは、配列のインプレース変更を許可しないADフレームワークにとってはしばしば簡単です。

# 返り値

  * `Z_smooth::Matrix{T}`: (P × (T_bar+1)) スムーズな状態
  * `P_smooth::Array{T,3}`: (P × P × (T_bar+1)) スムーズな共分散

# 例

```julia
Z_smooth, P_smooth = qkf_smoother(Z, P, Z_pred, P_pred, T_bar, Hn, Gn, H_aug, Φ_aug, n)
```
