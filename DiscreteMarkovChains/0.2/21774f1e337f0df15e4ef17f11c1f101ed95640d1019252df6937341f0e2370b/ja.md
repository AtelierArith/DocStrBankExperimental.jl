```
mean_recurrence_time(x)
```

# 定義

これは、プロセスが状態 $i$ から始まったときに、プロセスが状態 i に戻るための期待されるステップ数です。

# 引数

  * `x`: 何らかのマルコフ連鎖。

# 戻り値

i 番目のエントリが状態 $i$ の平均再発時間である 1D 配列。

# 注意事項

`x` は不可約でなければなりません（すなわち、エルゴード的である必要があります）。

# 例

```jldoctest mean_recurrence_time
using DiscreteMarkovChains
T = [
    0.1 0.2 0.7;
    0.3 0.0 0.7;
    0.4 0.4 0.2;
]
X = DiscreteMarkovChain(T)

mean_recurrence_time(X)

# 出力

3-element Array{Float64,1}:
 3.4615384615384603
 4.090909090909091
 2.1428571428571432
```

可約な連鎖がある場合、エラーは発生しませんが、出力は無意味になります。

```jldoctest mean_recurrence_time
T = [
    1.0 0.0 0.0;
    0.1 0.5 0.4;
    0.0 0.3 0.7;
]
X = DiscreteMarkovChain(T)

mean_recurrence_time(X)

# 出力

3-element Array{Float64,1}:
   1.0
 -Inf
 -Inf
```
