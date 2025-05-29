```
AdamOptimizer(η, ρ₁, ρ₂, δ)
```

Adamオプティマイザのインスタンスを作成します。

ここで、キャッシュは以下のように更新される第一および第二のモーメントで構成されています。

$$
B_1 \gets ((\rho_1 - \rho_1^t)/(1 - \rho_1^t))\cdot{}B_1 + (1 - \rho_1)/(1 - \rho_1^t)\cdot{}\nabla{}L,
$$

および

$$
B_2 \gets ((\rho_2 - \rho_1^t)/(1 - \rho_2^t))\cdot{}B_2 + (1 - \rho_2)/(1 - \rho_2^t)\cdot\nabla{}L\odot\nabla{}L.
$$

最終的な速度は次のように計算されます：

$$
\mathrm{velocity} \gets -\eta{}B_1/\sqrt{B_2 + \delta}.
$$

# 実装

*velocity* はメモリを節約するために入力に保存されます：

```julia
mul!(B, -o.method.η, /ᵉˡᵉ(C.B₁, scalar_add(racᵉˡᵉ(C.B₂), o.method.δ)))
```

ここで `B` は [`update!`] 関数への入力です。

アルゴリズムと推奨されるデフォルトは [goodfellow2016deep; page 301](@cite) から取られています。
