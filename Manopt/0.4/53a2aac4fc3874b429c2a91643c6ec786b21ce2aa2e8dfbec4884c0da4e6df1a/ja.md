```
Nesterov <: DirectionUpdateRule
```

## フィールド

  * `γ`
  * `μ` 強い凸性係数
  * `v` (=$=v_k$, $v_0=x_0$) 次の勾配評価点 `y_k` を計算するための中間点
  * `shrinkage` (`= i -> 0.8`) 各反復ごとの収縮 $β_k$ を計算する関数

$$
f
$$

が $L$-リプシッツかつ $μ$-強凸であると仮定します。与えられたもの：

  * ステップサイズ $h_k<\frac{1}{L}$ （[`GradientDescentState`](@ref) から）
  * `shrinkage` パラメータ $β_k$
  * 現在の反復 $x_k$
  * 前の反復からの中間値 $γ_k$ と $v_k$

次のステップを使用してネステロフ型の更新を計算します。詳細は [ZhangSra:2018](@cite) を参照してください。

1. 正の根 $α_k∈(0,1)$ を計算します：$α^2 = h_k\bigl((1-α_k)γ_k+α_k μ\bigr)$。
2. $$
    \bar γ_k+1 = (1-α_k)γ_k + α_kμ
    $$

    を設定します。
3. $$
    y_k = \operatorname{retr}_{x_k}\Bigl(\frac{α_kγ_k}{γ_k + α_kμ}\operatorname{retr}^{-1}_{x_k}v_k \Bigr)
    $$
4. $$
    x_{k+1} = \operatorname{retr}_{y_k}(-h_k \operatorname{grad}f(y_k))
    $$
5. $$
    v_{k+1} = \operatorname{retr}_{y_k}\Bigl(\frac{(1-α_k)γ_k}{\barγ_k}\operatorname{retr}_{y_k}^{-1}(v_k) - \frac{α_k}{\bar γ_{k+1}}\operatorname{grad}f(y_k) \Bigr)
    $$
6. $$
    γ_{k+1} = \frac{1}{1+β_k}\bar γ_{k+1}
    $$

次に、$x_k$ から $x_k+1$ への方向 $d = \operatorname{retr}^{-1}_{x_k}x_{k+1}$ が返されます。

# コンストラクタ

```
Nesterov(M::AbstractManifold, p::P; γ=0.001, μ=0.9, shrinkage = k -> 0.8;
    inverse_retraction_method=LogarithmicInverseRetraction())
```

ネステロフ加速を初期化します。ここで `x0` は `v` を初期化します。
