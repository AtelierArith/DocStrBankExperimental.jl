```
PCEuler(ggprime; theta=1/2, eta=1/2)
```

予測子修正オイラー法

# 引数

  * `ggprime::Function`: スカラー問題の場合、`ggprime` $= b\partial_x(b)$ 多次元問題の場合 `bbprime_k` $= \sum_{j=1...M, i=1...D} b^(j)_i \partial_i b^(j)_k$ ここで $b^(j)$ は j 番目のノイズチャネルによるノイズベクトルに対応します。問題がインプレースの場合 - インプレースの ggprime を提供する必要があります - 逆に、インプレースでない問題の指定の場合はその逆です。
  * `theta::Real`: ドリフト項における暗黙性の度合い。デフォルトで 0.5 に設定されています。
  * `eta::Real`: 拡散項における暗黙性の度合い。デフォルトで 0.5 に設定されています。

参考文献: Stochastics and Dynamics, Vol. 8, No. 3 (2008) 561–581 元の論文には ggprime の定義に誤植がありますので注意してください...
