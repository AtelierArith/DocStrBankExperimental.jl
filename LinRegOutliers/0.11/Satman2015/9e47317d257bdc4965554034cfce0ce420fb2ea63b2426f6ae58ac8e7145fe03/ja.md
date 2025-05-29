```
dominates(p1::Array, p2::Array)
```

p1の各要素がp2の対応する要素以上であり、かつp1の少なくとも1つの要素がp2の対応する要素より大きい場合にtrueを返します。

# 引数

  * `p1::Array`: n要素の数値配列。
  * `p2::Array`: n要素の数値配列。

# 例

```julia-repl
julia> dominates([1,2,3], [1,2,1])
true

julia> dominates([0,0,0,0], [1,0,0,0])
false
```

# 参考文献

Satman, Mehmet Hakan. "A new algorithm for detecting outliers in linear regression."  International Journal of statistics and Probability 2.3 (2013): 101.

Deb, Kalyanmoy, et al. "A fast elitist non-dominated sorting genetic algorithm for multi-objective optimization: NSGA-II."  International conference on parallel problem solving from nature. Springer, Berlin, Heidelberg, 2000.
