# 拡張ヘルプ

```
minkowski_sum(P1::VPolytope, P2::VPolytope;
              [apply_convex_hull]=true,
              [backend]=nothing,
              [solver]=nothing)
```

### 入力

  * `apply_convex_hull` – （オプション、デフォルト: `true`）`true`の場合、ペアごとの和を凸包アルゴリズムを使用して後処理します
  * `backend`           – （オプション、デフォルト: `nothing`）凸包で後処理するために使用される多面体計算のバックエンド; `default_polyhedra_backend(P1)`を参照してください
  * `solver`            – （オプション、デフォルト: `nothing`）線形計画を解決するために使用されるバックエンド; `default_lp_solver_polyhedra(N)`を参照してください

### アルゴリズム

頂点表現で得られる多面体は、`P1`と`P2`の頂点のすべての可能な和の凸包に対応する頂点で構成されます。
