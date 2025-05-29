```
mean_first_passage_time(x)
```

# 定義

これは、プロセスが状態 $i$ から始まったときに、プロセスが状態 $j$ に到達するための期待されるステップ数です。状態と自身の間の平均初回到達時間は0であると言います。

# 引数

  * `x`: 何らかのマルコフ連鎖。

# 戻り値

$$
(i,j)
$$

番目のエントリが状態 $i$ の平均再到達時間である行列。対角要素は0です。対角線は平均再到達時間を表すはずです。

# 注意事項

`x` は不可約でなければなりません（すなわち、エルゴード的である必要があります）。

# 例

```jldoctest mean_first_passage_time
using DiscreteMarkovChains
T = [
    0.1 0.2 0.7;
    0.3 0.0 0.7;
    0.4 0.4 0.2;
]
X = DiscreteMarkovChain(T)

mean_first_passage_time(X)

# 出力

3×3 Array{Float64,2}:
 0.0      3.40909  1.42857
 2.88462  0.0      1.42857
 2.69231  2.95455  0.0
```

もし可約な連鎖がある場合、エラーは発生しませんが、出力は無意味になります。

```jldoctest mean_first_passage_time
T = [
    1.0 0.0 0.0;
    0.1 0.5 0.4;
    0.0 0.3 0.7;
]
X = DiscreteMarkovChain(T)

mean_first_passage_time(X)

# 出力

3×3 Array{Float64,2}:
  0.0     -Inf  -Inf
 23.3333  NaN   -Inf
 26.6667  -Inf  NaN
```
