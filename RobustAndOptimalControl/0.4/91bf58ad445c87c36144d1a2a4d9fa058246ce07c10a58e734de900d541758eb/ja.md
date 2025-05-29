```
makeweight(low, f_mid, high)
makeweight(low, (f_mid, gain_mid), high)
```

ゲイン `low` からゼロ周波数で始まり、ゲイン `gain_mid` を経て、∞ でゲイン `high` に至る重み付け関数を作成します。

# 引数:

  * `low`: DC ゲインを指定する数値
  * `mid`: ゲインが 1 になる周波数を指定する数値、またはタプル `(freq, gain)`。`gain_mid` が指定されていない場合は、`high` と `low` の幾何平均が使用されます。
  * `high`: ∞ でのゲインを指定する数値

```@example
using ControlSystemsBase, Plots
W = makeweight(10, (5,2), 1/10)
bodeplot(W)
hline!([10, 2, 1/10], l=(:black, :dash), primary=false)
vline!([5], l=(:black, :dash), primary=false)
```
