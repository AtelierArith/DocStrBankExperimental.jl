```
quantilerank(itr, value; method=:inc)
```

コレクション `itr` に対する `value` の [0, 1] 区間内の分位数位置を計算します。

`method` キーワード引数を介して異なる定義を選択できます。`count_less` を `value` より小さい `itr` の要素数、`count_equal` を `value` と等しい `itr` の要素数、`n` を `itr` の長さ、`greatest_smaller` を `value` より小さい最大値、`smallest_greater` を `value` より大きい最小値とします。次に、`method` は以下の定義をサポートします：

  * `:inc` (デフォルト)：範囲 0 から 1 の値を返します。`value ∈ itr` の場合は `count_less / (n - 1)` を返し、そうでない場合は Hyndman と Fan (1996) の分位数の定義 7 に基づいて補間を適用します（Excel の `PERCENTRANK` および `PERCENTRANK.INC` に相当）。この定義は、デフォルトのパラメータを持つ [`quantile`](@ref) の下半連続逆関数に対応します。
  * `:exc`：範囲 0 から 1 の排他的な値を返します。`value ∈ itr` の場合は `(count_less + 1) / (n + 1)` を返し、そうでない場合は Hyndman と Fan (1996) の分位数の定義 6 に基づいて補間を適用します（Excel の `PERCENTRANK.EXC` に相当）。
  * `:compete`：`value ∈ itr` の場合は `count_less / (n - 1)` を返し、そうでない場合は補間なしで `(count_less - 1) / (n - 1)` を返します（MariaDB の `PERCENT_RANK`、dplyr の `percent_rank` に相当）。
  * `:tied`：補間なしで `(count_less + count_equal/2) / n` を返します。Roscoe, J. T. (1975) の定義に基づいています（SciPy の `percentileofscore` の `"mean"` 種類に相当）。
  * `:strict`：補間なしで `count_less / n` を返します（SciPy の `percentileofscore` の `"strict"` 種類に相当）。
  * `:weak`：補間なしで `(count_less + count_equal) / n` を返します（SciPy の `percentileofscore` の `"weak"` 種類に相当）。

!!! note
    `itr` に `NaN` または `missing` 値が含まれている場合、または `itr` に 2 つ未満の要素が含まれている場合、`ArgumentError` がスローされます。


# 参考文献

Roscoe, J. T. (1975). [Fundamental Research Statistics for the Behavioral Sciences](http://www.bryanburnham.net/wp-content/uploads/2014/07/Fundamental-Statistics-for-the-Behavioral-Sciences-v2.0.pdf#page=57)", 2nd ed., New York : Holt, Rinehart and Winston.

Hyndman, R.J and Fan, Y. (1996) "[Sample Quantiles in Statistical Packages](https://www.amherst.edu/media/view/129116/original/Sample+Quantiles.pdf)", *The American Statistician*, Vol. 50, No. 4, pp. 361-365.

# 例

```julia-repl
julia> using StatsBase

julia> v1 = [1, 1, 1, 2, 3, 4, 8, 11, 12, 13];

julia> v2 = [1, 2, 3, 5, 6, missing, 8];

julia> v3 = [1, 2, 3, 4, 4, 5, 6, 7, 8, 9];

julia> quantilerank(v1, 2)
0.3333333333333333

julia> quantilerank(v1, 2, method=:exc), quantilerank(v1, 2, method=:tied)
(0.36363636363636365, 0.35)

# 欠損エントリを含むベクトルには `skipmissing` を使用します。
julia> quantilerank(skipmissing(v2), 4)
0.5

# 複数の値の分位数ランクを計算するために `Ref` を使ってブロードキャスティングを使用します
julia> quantilerank.(Ref(v3), [4, 8])
2-element Vector{Float64}:
 0.3333333333333333
 0.8888888888888888
```
