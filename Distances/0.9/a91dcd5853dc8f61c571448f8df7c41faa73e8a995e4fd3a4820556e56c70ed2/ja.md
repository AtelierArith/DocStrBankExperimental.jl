```
PeriodicEuclidean(L)
```

長方形の周期的領域（すなわち、トーラスまたは円柱）上にユークリッド距離を作成します。次元ごとの周期はベクトル `L` に含まれています：

$$
\sqrt{\sum_i(\min\mod(|x_i - y_i|, p), p - \mod(|x_i - y_i|, p))^2}.
$$

周期性のない次元には、それぞれの成分に `Inf` を入れてください。

# 例

```jldoctest
julia> x, y, L = [0.0, 0.0], [0.75, 0.0], [0.5, Inf];

julia> evaluate(PeriodicEuclidean(L), x, y)
0.25
```
