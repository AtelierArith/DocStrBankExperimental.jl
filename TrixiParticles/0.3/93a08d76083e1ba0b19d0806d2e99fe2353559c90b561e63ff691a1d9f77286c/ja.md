```
BlendedGradientCorrection()
```

安定性の問題を軽減するためにブレンドされた勾配を計算します [`GradientCorrection`](@ref) は [Bonet (1999)](@cite Bonet1999) によって説明されています。

これにより、以下が計算されます。

$$
\tilde\nabla A_i = (1-\lambda) \nabla A_i + \lambda L_i \nabla A_i
$$

ここで、$0 \leq \lambda \leq 1$ はブレンド係数です。

# 引数

  * `blending_factor`: 補正されたSPH勾配と通常のSPH勾配の間のブレンド係数。
