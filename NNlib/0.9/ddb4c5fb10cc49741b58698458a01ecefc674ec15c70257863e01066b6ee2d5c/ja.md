```
dropout([rng], A, p; [dims])
```

`A`の各要素が確率`p`でゼロに置き換えられるか、そうでなければ`1/(1-p)`で乗算された配列を返します。

デフォルトでは、すべての要素は独立して扱われます。キーワード`dims=1`を指定すると、1番目のインデックスの各値に対して選択が行われ、すなわち行列の各行がゼロかそうでないかが決まります。

オプションの最初の引数は使用される乱数生成器です。

# 例

```julia-repl
julia> dropout(ones(2, 10), 0.2)
2×10 Matrix{Float64}:
 1.25  1.25  0.0   1.25  1.25  1.25  1.25  1.25  1.25  1.25
 1.25  1.25  1.25  0.0   1.25  1.25  0.0   1.25  1.25  1.25

julia> mean(dropout(ones(10^4, 5), 0.2), dims=1)
1×5 Matrix{Float64}:
 0.998  1.00075  0.99125  0.99575  1.00075

julia> dropout(ones(5, 5), 0.7, dims=1)  # 行全体が同じ
5×5 Matrix{Float64}:
 3.33333  3.33333  3.33333  3.33333  3.33333
 0.0      0.0      0.0      0.0      0.0
 0.0      0.0      0.0      0.0      0.0
 3.33333  3.33333  3.33333  3.33333  3.33333
 0.0      0.0      0.0      0.0      0.0

julia> mean(dropout(ones(10^4, 5), 0.3, dims=1), dims=1)
1×5 Matrix{Float64}:
 1.00571  1.00571  1.00571  1.00571  1.00571
```
