```
unzip(vs)
unzip(v1, v2, ...)
unzip(r::Function, a, b)
```

ベクトルで表された点の集合を取り（例えば `r(t)=[sin(t),cos(t)], r.([1,2,3])` のように返される）、収集された x 値、y 値、オプションで z 値のタプルを返します。

`SplitApplyCombine` の `invert` 関数のラッパーです。

引数がカンマ区切りのベクトルのコレクションとして指定されている場合、これらは結合されて渡されます。

引数が関数と2つの端点である場合、その関数は `a` と `b` の間の点で評価されます。単変量の場合、点は適応的に選択されます。

これは、データがベクトルの形でより便利に表現される場合にプロットに役立ちますが、プロットインターフェースは収集された x および y 値を必要とします。

例:

```
using Plots
r(t) = [sin(t), cos(t)]
rp(t) = [cos(t), -sin(t)]
plot(unzip(r, 0, 2pi)...)  # calls plot(xs, ys)

t0, t1 = pi/6, pi/4

p, v = r(t0), rp(t0)
plot!(unzip(p, p+v)...)  # connect p to p+v with line

p, v = r(t1), rp(t1)
quiver!(unzip([p])..., quiver=unzip([v]))
```

`Plots` パッケージの `unzip` に基づいています。`SplitApplyCombine` の `invert` を通じて実装されています。

注意: 点のベクトル `xs` がそれぞれ長さ `2` の場合、類似の機能は `(first.(xs), last.(xs))` になります。各点が長さ `3` の場合、`second(x)=x[2]` を用いて、類似の機能は `(first.(xs), second.(xs), last.(xs))` になります。

```
