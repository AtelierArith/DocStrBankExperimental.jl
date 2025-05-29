```
ProximalLocationScaleEntropy()
```

位置-スケール分布のエントロピーのための近接演算子は、次のように定義されます。

$$
    \mathrm{prox}(\lambda) = \argmin_{\lambda^{\prime}} - \mathbb{H}(q_{\lambda^{\prime}}) + \frac{1}{2 \gamma_t} \left\lVert \lambda - \lambda^{\prime} \right\rVert ,
$$

ここで、$\gamma_t$は近接演算子と共に使用される最適化器のステップサイズです。これは、変分ファミリーが`<:VILocationScale`であり、最適化器が次のいずれかであることを前提としています。

  * `DoG`
  * `DoWG`
  * `Descent`

ELBOの最大化のために、この近接演算子がエントロピーを処理するため、ELBOの勾配推定器はエントロピー項を無視しなければなりません。つまり、`RepGradELBO`の`entropy`キーワード引数は次のいずれかでなければなりません。

  * `ClosedFormEntropyZeroGradient`
  * `StickingTheLandingEntropyZeroGradient`
