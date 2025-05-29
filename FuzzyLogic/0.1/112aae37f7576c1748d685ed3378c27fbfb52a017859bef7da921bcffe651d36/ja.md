```julia
struct CentroidDefuzzifier <: FuzzyLogic.AbstractDefuzzifier
```

セントロイドデフuzzifier。集約された出力関数 $f$ と出力変数のドメイン $[a, b]$ が与えられたとき、デフuzzified出力は次のように計算されるセントロイドです。

$$
\frac{∫_a^bxf(x)\textrm{d}x}{∫_a^bf(x)\textrm{d}x}.
$$

### パラメータ

  * `N::Int64`: 積分のためのサブ区間の数、デフォルトは100です。

## アルゴリズム

積分は台形法を使用して数値的に計算されます。
