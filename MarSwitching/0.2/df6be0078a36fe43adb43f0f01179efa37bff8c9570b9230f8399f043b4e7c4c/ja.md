```
get_std_errors(model::MSM)
```

推定されたパラメータの標準誤差を返します。誤差は対数尤度関数の有限差分ヘッセ行列を用いて計算されます。

出力は、モデルの `raw_params` フィールドによって与えられる順序の標準誤差のベクトルです。

この公式は、ヘッセ行列の逆（ムーア・ペンローズ）の二乗対角値です：

$$
(-\frac{\partial^2 \mathcal{L}(\mathbf{\theta})}{\partial \mathbf{\theta} \mathbf{\theta}'})^{-1}
$$
