```
ConjugateGradientBealeRestart <: DirectionUpdateRule
```

更新ルールは、最後の2つの勾配がほぼ直交している場合、純粋な勾配を降下方向として使用する再起動を必要とすることがあります。詳細は[HagerZhang:2006; page 12](@cite)を参照してください（プレプリントでは、ジャーナルのページ番号で46ページ）。この手法は、1972年の彼の論文に由来するE. Bealeにちなんで名付けられました[Beale:1972](@cite)。この手法は、既存の[`DirectionUpdateRule`](@ref) `direction_update`に対する*デコレーター*として機能します。

[`ConjugateGradientDescentState`](@ref)`cgs`から取得した最後の$p_k,X_k$と現在の$p_{k+1},X_{k+1}$の反復および勾配をそれぞれ取得します。

次に、再起動が行われ、以下の場合に$β_k = 0$が返されます。

$$
    \frac{ ⟨X_{k+1}, P_{p_{k+1}\gets p_k}X_k⟩}{\lVert X_k \rVert_{p_k}} > ξ,
$$

ここで、$P_{a\gets b}(⋅)$は点$a$から点$b$への接空間からのベクトル輸送を示し、$ξ$は`threshold`です。デフォルトの閾値は、[Powell:1977](@cite)で推奨されているように`0.2`に設定されています。

# コンストラクタ

```
ConjugateGradientBealeRestart(
    direction_update::D,
    threshold=0.2;
    manifold::AbstractManifold = DefaultManifold(),
    vector_transport_method::V=default_vector_transport_method(manifold),
)
```
