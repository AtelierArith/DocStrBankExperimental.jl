```
Hist(edges; left = true, closed = true)
```

`edges`で定義されたビンパーティションを持つヒストグラムを作成します。

  * `left`が真の場合、ビンは左閉じになります。
  * `closed`が真の場合、端のビンは閉じになります。

      * 例えば、2つのビンのヒストグラム $[a, b), [b, c)$ と $[a, b), [b, c]$ の違いです。

# 例

```
o = fit!(Hist(-5:.1:5), randn(10^6))

# おおよその統計
using Statistics

mean(o)
var(o)
std(o)
quantile(o)
median(o)
extrema(o)
```
