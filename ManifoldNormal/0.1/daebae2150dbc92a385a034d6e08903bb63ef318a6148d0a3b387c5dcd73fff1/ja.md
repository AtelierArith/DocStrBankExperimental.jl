```
adjoint_noise(noise::ActionNoise{<:GroupOperationAction})
```

もしノイズが群作用によって定義されている場合、反対側にスイッチされた作用に対する対応するノイズを計算します。これは次の恒等式に基づいています。

$$
χ \exp(ξ) = \exp(χ ξ χ^{-1}) χ
$$

および

$$
\exp(ξ) χ = χ \exp(χ^{-1} ξ χ)
$$
