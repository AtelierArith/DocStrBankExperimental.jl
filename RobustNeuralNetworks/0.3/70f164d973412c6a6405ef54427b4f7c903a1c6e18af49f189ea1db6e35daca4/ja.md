```
mutable struct ExplicitLBDNParams{T, N, M}
```

明示的LBDNパラメータ構造体。

これらのパラメータは、モデル評価に使用されるリプシッツ境界付き深層ネットワークの明示的な形式を定義します。パラメータは`NTuple`に格納されており、`NTuple`の各要素はネットワークの単一層のパラメータです。タプルは配列のベクトルよりも高速に操作できます。

明示的なLBDNのパラメータ化に関する詳細は、[Wang et al. (2023)](https://proceedings.mlr.press/v202/wang23v.html)を参照してください。
