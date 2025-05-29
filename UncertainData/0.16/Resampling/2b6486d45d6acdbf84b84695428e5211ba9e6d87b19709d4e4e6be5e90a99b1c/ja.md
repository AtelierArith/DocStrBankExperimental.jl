```
resample(x::AbstractUncertainIndexValueDataset, resampling::BinnedMeanResampling)
```

不規則に間隔を置かれた不確実なデータを正規のインデックスグリッドに変換し、各ビンの値の平均を取ります。

各インデックスビンの分布は、`x`のすべてのインデックス値を`resampling.n`回再サンプリングし、それらのインデックスドローをビンにマッピングすることによって得られます。同時に、`x`の値も再サンプリングされ、対応するビンに配置されます。最後に、各ビンの平均が計算されます。合計で、`length(x)*resampling.n`のドローがビンに分配され、最終的な平均推定値が形成されます。

各ビンの平均値のベクトルを返します。

`x`のポイントは独立であると仮定します。

## 例

```julia
vars = (1, 2)
npts, tstep = 100, 10
d_xind = Uniform(2.5, 15.5)
d_yind = Uniform(2.5, 15.5)
d_xval = Uniform(0.01, 0.2)
d_yval = Uniform(0.01, 0.2)

X, Y = example_uncertain_indexvalue_datasets(ar1_unidir(c_xy = 0.5), npts, vars, tstep = tstep,
    d_xind = d_xind, d_yind = d_yind,
    d_xval = d_xval, d_yval = d_yval);

n_draws = 10000 # 不確実な値ごとのドロー数
time_grid = 0:50:1000

# XとYの両方を再サンプリングして、同じ時間インデックスにし、
# 各ビンの平均を取ります。
resampled_dataset = resample(X, BinnedMeanResampling(time_grid, n_draws))
resampled_dataset = resample(Y, BinnedMeanResampling(time_grid, n_draws))
```
