```
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedResampling{RawValues}) -> Tuple(Vector, Vector{Vector})
```

`x`の各要素を`binning.n`で与えられた回数だけ再サンプリングします。再サンプリング後、値をそのインデックスに従って、`binning.left_bin_edges`で与えられた`N`個のビンに分配します。

## 戻り値

`N`個の異なるビンの中心と、再サンプリングされたインデックスが`N`個の異なるビンに入る再サンプリングされた値の`N`長のベクトルを含むタプルを返します。

## 例

```julia
# 不均等に間隔を空けた時間インデックスを持つデータの例
npts = 300
time, vals = sort(rand(1:1000, npts)), rand(npts)

# インデックスと値に不確実性を追加し、 
# UncertainIndexValueDatasetとして表現します 
utime = [UncertainValue(Normal, t, 10) for t in time]
uvals = [UncertainValue(Normal, v, 0.1) for v in vals]

udata = UncertainIndexValueDataset(utime, uvals)

# 時間インデックス100から900までの25時間ステップ幅のビンにデータをビン分けし、 
# 各ビンの生の値のベクトルを返します。これは、各不確実な
# データポイントを10000回再サンプリングし、それらの引き出しをビンに分配することによって行います。
left_bin_edges = 100:25:900
n_draws = 10000
binning = BinnedResampling(RawValues, left_bin_edges, n_draws)

bin_centers, bin_draws = bin(udata, binning)
```
