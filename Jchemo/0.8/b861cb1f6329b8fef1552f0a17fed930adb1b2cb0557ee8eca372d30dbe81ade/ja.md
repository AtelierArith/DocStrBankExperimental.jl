```
rd(X, Y; typ = :cor)
rd(X, Y, weights::Weight; typ = :cor)
```

冗長性係数 (Rd) を計算します。

  * `X` : 行列 (n, p)。
  * `Y` : 行列 (n, q)。
  * `weights` : 観測値の重み (n)。    `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `typ` : 可能な値は次のとおりです: `:cor` (相関)、    `:cov` (未修正の共分散)。

`X` と `Y` の各列との間の冗長性係数を返します。すなわち、各 k = 1,...,q に対して:

  * 平均 {cor(xj, yk)^2 ;  j = 1, ..., p }

引数 `typ` に応じて、相関は (未修正の) 共分散に置き換えることができます。

Tenenhaus 1998 年のセクション 2.2.1 p.10-11 を参照してください。

## 参考文献

Tenenhaus, M., 1998. La régression PLS: théorie et pratique.  Editions Technip, Paris.

## 例

```julia
using Jchemo
X = rand(5, 10)
Y = rand(5, 3)
rd(X, Y)
```
