```
an_element(P::AbstractPolyhedron; [solver]=default_lp_solver(eltype(P)))
```

多面体の要素を返します。

### 入力

  * `P`       – 多面体
  * `solver`  – （オプション、デフォルト: `default_lp_solver(N)`）LPソルバー

### 出力

多面体の要素、または多面体が空である場合はエラー。

### アルゴリズム

要素は実現可能性線形計画を解くことによって得られます。
