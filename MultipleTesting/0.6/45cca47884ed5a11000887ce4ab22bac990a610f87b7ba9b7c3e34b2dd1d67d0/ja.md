フラットグレナンダーπ₀推定量

グレナンダー推定量における最長の定数区間を見つけることでπ₀を推定します。

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, FlatGrenander())
0.42553191489361697
```

# 参考文献

Langaas, M., Lindqvist, B.H., and Ferkingstad, E. (2005). 真の帰無仮説の割合を推定する、DNAマイクロアレイデータへの応用を伴う。ロイヤル統計学会誌：シリーズB（統計的方法論）67, 555–572。
