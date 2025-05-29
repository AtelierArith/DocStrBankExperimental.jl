```
resample(x::AbstractUncertainIndexValueDataset, resampling::BinnedWeightedResampling;
    nan_threshold = 0.0)
```

不規則に間隔を空けた不確実なデータを、規則的なインデックスグリッドに変換します。

各インデックスビンの分布は、`x` のすべてのインデックス値を `resampling.n` 回再サンプリングし、`resampling.weights` に従ってサンプリングし、これらのインデックスドローをビンにマッピングすることによって得られます。同時に、`x` の値も再サンプリングされ、対応するビンに配置されます。合計で、`length(x)*resampling.n` のドローがビンに分配され、最終的なKDEが形成されます。

`UncertainIndexValueDataset` を返します。`i` 番目のビンの値の分布は、`i` 番目のビンに落ちるドローに対するカーネル密度推定（KDE）によって近似されます。

`x` の点が独立であると仮定します。

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

left_bin_edges = 0:50:1000
n_draws = 10000
wts = Weights(rand(length(X)))
resampling = BinnedWeightedResampling(left_bin_edges, wts, 10)
resampled_dataset = resample(X, resampling)
```
