```
  lcc(haystack,needle)
```

`haystack`内のスライディングウィンドウと`needle`との間のローカル（ピアソン）相関係数を直接計算します。

# 例

`haystack`が実数のテンソルで、`needle`が同じ次元の小さなテンソルであり、`haystack`内で位置を特定しようとしているとします。`needle`はスケーリングおよび平行移動されている可能性があることに注意してください。

最大LCCの位置は、`needle`と`haystack`のスライディングウィンドウとの間の最良の一致です。

```jldoctest
julia> using FastLocalCorrelationCoefficients

julia> haystack = rand(2^10,2^10);

julia> needle = rand(1) .* haystack[42:47, 45:50] .+ rand(1);

julia> c = lcc(haystack,needle);

julia> best_correlated(c)
CartesianIndex(42, 45)
```
