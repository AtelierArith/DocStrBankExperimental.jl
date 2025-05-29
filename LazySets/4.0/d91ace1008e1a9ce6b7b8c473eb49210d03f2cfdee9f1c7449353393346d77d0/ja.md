# 拡張ヘルプ

```
volume(P::AbstractPolytope; backend=default_polyhedra_backend(P))
```

### 入力

  * `backend` – (オプション、デフォルト: `default_polyhedra_backend(P)`) 多面体計算のためのバックエンド; 詳細については[Polyhedraのドキュメント](https://juliapolyhedra.github.io/)を参照してください

### アルゴリズム

体積は`Polyhedra`ライブラリによって計算されます。
