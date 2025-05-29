```
make_theta0s(theta0::T, ball_radius::T, pdf, nwalkers;
                  ball_radius_halfing_steps=7, # この回数だけボールを小さくする
                  ntries=100*nwalkers, # 各ボール半径あたりの試行回数
                  hasblob=false) where T
```

theta0からのボール内で非ゼロ密度のtheta0sを見つけようとします。`emcee`と一緒に使用します。

例

```
pdf = x-> -sum(x.^2)
nwalkers = 100
samples = emcee(pdf, make_theta0s([0.0, 0.0], [0.1, 0.1], pdf, nwalkers), nburnin=0, use_progress_meter=false);
```
