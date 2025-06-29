```
NoBloating{EM, SO, IT} <: AbstractApproximationModel
```

膨張なし、または離散時間の近似モデル。

### フィールド

  * `exp`     – 指数法
  * `setops`  – 集合演算法
  * `inv`     – （オプション、デフォルト: `false`）`true`の場合、状態行列が可逆であると仮定し、その逆行列を`Φ`関数で使用します。

### アルゴリズム

変換は次のとおりです：

  * $$
    Φ ← \exp(Aδ)
    $$
  * $$
    Ω_0 ← \mathcal{X}_0
    $$
  * $$
    V(k) ← Φ₁(A, δ)U(k)
    $$

    , $k ≥ 0$。

関数$Φ₁(A, δ)$は[`Φ₁`](@ref)で定義されています。$U$は時間変化する非決定論的入力集合のシーケンスであることを許可します。

さらに、[BogomolovFFVPS18; Eq. (14)](@citet)も参照してください。
