```julia
copula_entropy(x; kwargs...)

```

コピュラエントロピーを推定するには

1. 経験的コピュラを計算します（[`empirical_copula`](@ref)も参照）;
2. Kraskov法を使用してエントロピーを推定します（キーワードパラメータについては[`entropy_knn`](@ref)を参照）[1]。

返されるコピュラエントロピーは負の相互情報量です[2]。

# 参考文献

1. Alexander Kraskov, Harald Stögbauer and Peter Grassberger. "Estimating mutual information." Physical review, 2004.
2. Jian Ma and Zengqi Sun. "Mutual information is copula entropy." Tsinghua Science & Technology, 2011.
