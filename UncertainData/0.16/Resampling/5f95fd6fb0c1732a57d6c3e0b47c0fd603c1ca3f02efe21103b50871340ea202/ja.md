```
bin(x::AbstractUncertainIndexValueDataset, 
    binning::BinnedWeightedResampling{RawValues}) -> Tuple(Vector, Vector{Vector})
```

`x`の各要素を指定された回数だけ再サンプリングします。再サンプリング後、`binning.left_bin_edges`で定義された`N-1`要素のグリッドによって与えられた`N`個のビンに、インデックスに応じて値を分配します。合計で、`length(x)*binning.n`の引き出しがビンに分配されます。`x[i]`が再サンプリングされる正確な回数は、`binning.weights[i]`によって与えられます（確率重みは常に1に正規化されます）。

## 戻り値

`N`個の異なるビンの中心と、再サンプリングされた値の`N`長のベクトルを含むタプルを返します。再サンプリングされたインデックスが`N`個の異なるビンに入るものです。

## 例

```julia
using Plots, UncertainData
# 不均等に間隔を空けた時間インデックスを持つサンプルデータ
function ar1(n::Int, x0 = 0.5, p = 0.3)
    vals = zeros(n)
    [vals[i] = vals[i - 1]*p + rand()*0.5 for i = 2:n]
    return vals
end

npts = 50
time, vals = sort(rand(1:1000, npts)), ar1(npts)

# インデックスと値に不確実性を追加し、 
# UncertainIndexValueDatasetとして表現します 
utime = [UncertainValue(Normal, t, 5) for t in time]
uvals = [UncertainValue(Normal, v, 0.03) for v in vals]

udata = UncertainIndexValueDataset(utime, uvals)

# 時間インデックス100から900までの25時間幅のビンにデータをビン分けし、 
# 各ビンの生の値のベクトルを返します。 
# 各不確実なデータポイントを平均10000回再サンプリングし、 
# それらの引き出しをビンに分配します。 
time_grid = 100:40:900
n_draws = 5000
# 奇数インデックスの値が偶数インデックスの値の3倍の確率で 
# サンプリングされるようにします。
wts = Weights([i % 2 == 0 ? 1 : 3 for i = 1:length(udata)])
binning = BinnedWeightedResampling(RawValues, time_grid, wts, n_draws)

bin_centers, bin_draws = bin(udata, binning);
```
