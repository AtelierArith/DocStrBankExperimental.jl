```
BerendsenBarostat(pressure, coupling_const; compressibility=4.6e-5u"bar^-1",
                  max_scale_frac=0.1, n_steps=1)
```

圧力を制御するためのベルンデセンバロスタ。

ボックスのスケーリングファクターは、毎 `n_steps` ステップごとに次のようになります。

$$
\mu = 1 - \frac{\kappa_T \delta t}{3 \tau} ( P_0 - P )
$$

分数変化は `max_scale_frac` に制限されています。

このバロスタは、シミュレーションアーティファクトを引き起こす可能性があるため、注意して使用する必要があります。
