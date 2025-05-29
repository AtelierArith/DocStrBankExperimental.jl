```
struct HamiltonJacobiEvolution{O}
```

ハミルトン-ヤコビ進化方程式と再初期化方程式を解くための標準的な前進オイラー時間有限差分法で、順次または並列での次数 `O` 有限要素に対応しています。

OsherとFedkiwによるスキームに基づいています ([link](https://doi.org/10.1007/b98879))。

# パラメータ

  * `stencil::Stencil`: 単一ステップHJ方程式と再初期化方程式のための空間有限差分ステンシル。
  * `model`: `CartesianDiscreteModel`。
  * `space`: レベルセット関数のためのFE空間
  * `perm`: 順序ベクトル
  * `params`: 追加のパラメータのタプル
  * `cache`: ステンシルキャッシュ
