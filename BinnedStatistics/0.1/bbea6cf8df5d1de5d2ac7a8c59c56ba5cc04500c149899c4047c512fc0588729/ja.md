配列のy値に対して、いくつかのx値の配列に沿った高速なビン統計を計算します。基本的には、選択した統計が各ビンで計算されるヒストグラムです。

この関数は、既存のscipy.stats.binned_statistic関数のアナログですが、ネイティブJuliaで書かれており、この実装はSciPyバージョンよりも高速です！

ビンのエッジ、ビンの中心、および対応するビン統計を返します。現在実装されている統計操作は、合計、平均、中央値、分散、標準偏差、およびカスタム関数を渡すオプションです。中央値/カスタム関数の実装は、他のものよりもはるかに遅く（合計の約30倍遅い）、最も高速ですが、scipy.stats.binned_statisticに合わせるために含まれています。簡単に改善できますが、今のところ怠惰な状態に置かれています。

使用例：

```julia
x = rand(2048,2048); y = rand(2048,2048)
edges, centers, binnedSum = binnedStatistic(x,y,nbins=500,statistic=:sum)

edges, centers, binnedSum = binnedStatistic(x,y) #デフォルトは100ビンの:sum

edges, centers, binnedVar = binnedStatistic(x,y,statistic=:var) #各ビンの分散を計算し、デフォルトの100ビンを残す

f(x) = sum(x.^2) #ユーザー定義関数の例、ベクトル化する必要がありますが、単一のスカラーFloat64値を返す必要があります
edges, centers, binnedF = binnedStatistic(x,y,statistic=:f,f=f)
```

これは技術的には上記の既存のヒストグラム機能を使用して行うことができますが、非常に遅く、この新しい方法は約15〜20倍速いです。`StatsBase`の既存のヒストグラムルーチンを使用した例：

```julia
function histSum(x::Array,y::Array,bins::Int=100) #ヒストグラムの各ビンで合計を計算し、StatsBaseの既存の機能を使用
    h = fit(Histogram, vec(x), aweights(y), nbins=bins)
    h.edges, h.weights
end
```

`julia> x = rand(2048,2048); y = rand(2048,2048) julia> using BenchmarkTools julia> @btime histSum(x,y)     268.793 ms (8 allocations: 1.20 KiB)`

この新しい高速バージョンを使用すると、約15〜20倍のスピードアップが得られます：

`julia> @btime binnedStatistic(x,y)     14.165 ms (3 allocations: 1.83 KiB)`

これらのテストは、Linux Mint 20.3 Cinnamonを実行しているシステム上で、Intel Core i7-1065G7 CPU（4コア@ 1.3 GHz）を使用してJulia 1.6.1で実施されました。
