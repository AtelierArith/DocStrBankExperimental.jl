```
sinc_interpolate_sum(arr, new_length)
```

1Dの`arr`の`sinc`補間を新しい配列サイズ`new_size`で計算します。このメソッドは、明示的な合計評価のため遅く、FFTベースの評価ではありません。

# 例

```jldoctest
julia> sinc_interpolate_sum([1.0, 2.0, 3.0, 4.0], 8)
8-element Array{Float64,1}:
 1.0
 1.7825353626292277
 2.0
 2.1220659078919377
 3.0
 4.1592491794681985
 4.0
 2.0735615442829793
```
