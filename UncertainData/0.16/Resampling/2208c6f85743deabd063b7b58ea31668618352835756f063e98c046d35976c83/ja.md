```
resample(x::AbstractUncertainIndexValueDataset, resampling::BinnedResampling{UncertainScalarKDE};
    bin_repr::Symbol = :kde, nan_threshold = 0.0)
```

不規則に間隔を置かれた不確実なデータを、規則的なインデックスグリッドに変換します。各インデックスビン内の分布は、`x`のすべてのインデックス値を`resampling.n`回再サンプリングし、それらのインデックスドローをビンにマッピングすることによって得られます。同時に、`x`の値も再サンプリングされ、対応するビンに配置されます。合計で、`length(x)*resampling.n`のドローがビンに分配され、最終的なKDEを形成します。

`UncertainIndexValueDataset`を返します。`i`-thビン内の値の分布は、`i`-thビンに落ちるドローに対するカーネル密度推定（KDE）によって近似されます。

`x`内の点が独立であると仮定します。

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
resampling = BinnedResampling(time_grid, n_draws)

# XとYの両方を再サンプリングして、同じ時間インデックスにします。
resampled_dataset = resample(X, resampling)
resampled_dataset = resample(Y, resampling)
```
