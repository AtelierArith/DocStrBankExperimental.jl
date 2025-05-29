```
Mosaic(T::Type, S::Type)
```

モザイクプロットを生成するためのデータ構造で、2つのカテゴリ変数の比較を行います。

# 例

```
using OnlineStats, Plots
x = [rand() > .8 for i in 1:10^5]
y = rand([1,2,2,3,3,3], 10^5)
o = fit!(Mosaic(Bool, Int), zip(x, y))
plot(o)
```
