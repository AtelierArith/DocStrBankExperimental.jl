```
qkf_smoother!(
    Z::AbstractMatrix{T},      # フィルタリングされた状態   (P × (T_bar+1))
    P::AbstractArray{T, 3},    # フィルタリングされた共分散 (P × P × (T_bar+1))
    Z_pred::AbstractMatrix{T}, # 一歩先の予測された状態 (P × T_bar)
    P_pred::AbstractArray{T,3},
    T_bar::Int,
    Hn::Matrix{T},  Gn::Matrix{T},  H_aug::Matrix{T},  Φ_aug::Matrix{T},
    dof::Int
) where {T<:Real}
```

**インプレース**での後方スムージングを行うための二次カーマンフィルタ（QKF）。

# 説明

`t=1..T_bar`からの前方フィルタリングされた推定値`(Z, P)`、さらに一歩先の予測`(Z_pred, P_pred)`と、次元削減を扱う特別な行列（H*aug, G*aug）を考慮して、この関数は`Z[:,t]`と`P[:,:,t]`を`t = T_bar-1 .. 1`の後方の方法で計算し、スムーズな推定値`(Zₜ|T*bar, PZₜ|T*bar)`を生成します。

## 数学的形式（後方パス）

1. Fₜ = (H̃ₙPᵗ|ᵗᶻH̃ₙ')(H̃ₙΦ̃G̃ₙ)'(H̃ₙPᵗ⁺¹|ᵗᶻH̃ₙ')⁻¹を計算しますが、数値的安定性のために明示的な逆行列ではなく解法を使用して実装します。
2. 次に、（H̃ₙ変換空間で）更新します：H̃ₙZₜ|ₜ = H̃ₙZₜ|ₜ + Fₜ(H̃ₙZₜ₊₁|ₜ - H̃ₙZₜ₊₁|ₜ)
3. 共分散についても同様に： (H̃ₙPᵗ|ᵀᶻH̃ₙ') = (H̃ₙPᵗ|ᵗᶻH̃ₙ') + Fₜ[(H̃ₙPᵗ⁺¹|ᵀᶻH̃ₙ') - (H̃ₙPᵗ⁺¹|ᵗᶻH̃ₙ')]Fₜ'
4. 最後に、必要に応じて完全な（Vec/augmented）空間で`Zₜ|T`と`Pᵗ|ᵀᶻ`を取得するために戻します。

# 引数

  * `Z::AbstractMatrix{T}`: 入力時、`Z[:,t]` = `Zₜ|T`が各`t`に対して。出力時、スムーズな状態`Zₜ|T`が含まれます。
  * `P::AbstractArray{T,3}`: 入力時、`P[:,:,t]` = `Pᵗ|ᵀᶻ`。出力時、`P[:,:,t]` = `Pᵗ|ᵀᶻ`。
  * `Z_pred::AbstractMatrix{T}`, `P_pred::AbstractArray{T,3}`: 前方パスからの一歩先の予測された状態/共分散、すなわち`Z_pred[:,t] = Zₜ|ₜ`、`P_pred[:,:,t] = P^Zₜ|ₜ`。
  * `T_bar::Int`: 総時間ステップ（時間0を除く）。
  * `Hn::Matrix{T}`, `Gn::Matrix{T}`: ブロック`(x xᵀ)`のVec/Vech変換のための選択/重複演算子。通常サイズは`(n(n+1) × n(n+3)/2)`またはそれに類似。
  * `H_aug::Matrix{T}`, `Φ_aug::Matrix{T}`: QKF再帰で使用される拡張バージョン（H*aug, G*aug）。
  * `dof::Int`: 次元パラメータ（しばしば`n`または`P`）。モデルに合わせて調整します。

# 注意事項

  * この関数は`t = T_bar-1`から`t = 1`まで後方に実行され、最終値`(Z[:, T_bar], P[:,:, T_bar])`を端条件として使用します（`Z_{T_bar|T_bar}, P^Z_{T_bar|T_bar}`）。
  * ADライブラリが破壊的更新をサポートしている場合、このアプローチはADフレンドリーであるべきです。そうでない場合は、インプレースでないバージョン`qkf_smoother`を検討してください。

# 例

前方フィルタをすでに実行していると仮定しますので、次のものがあります：Z, P, Z*pred, P*pred、さらに特別な行列。

```
qkf_smoother!(Z, P, Z_pred, P_pred, T_bar, Hn, Gn, H_aug, Φ_aug, n)
```
