```
tohrep(P::VPolytope; [backend]=default_polyhedra_backend(P))
```

頂点表現の多面体を制約表現の多面体に変換します。

### 入力

  * `P`       – 頂点表現の多面体
  * `backend` – （オプション、デフォルト: `default_polyhedra_backend(P)`）多面体計算のためのバックエンド; 詳細については[Polyhedraのドキュメント](https://juliapolyhedra.github.io/)を参照してください

### 出力

`P`の制約表現としての`HPolytope`。

### 注意事項

変換は数値型を保持しない場合があります（例: `N == Float32`）バックエンドによって異なります。
