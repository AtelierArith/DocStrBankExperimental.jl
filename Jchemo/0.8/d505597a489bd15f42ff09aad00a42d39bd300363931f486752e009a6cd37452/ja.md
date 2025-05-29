```
findmax_cla(x)
findmax_cla(x, weights::Weight)
```

`x`の中で最も頻繁に出現するレベルを見つけます。

  * `x` : カテゴリ変数。
  * `weights` : 観測値の重み (n)。`Weight`型のオブジェクト（例えば、`mweight`関数によって生成されたもの）。

同点の場合、関数は最初のものを返します。

## 例

```julia
using Jchemo

x = rand(1:3, 10)
tab(x)
findmax_cla(x)
```
