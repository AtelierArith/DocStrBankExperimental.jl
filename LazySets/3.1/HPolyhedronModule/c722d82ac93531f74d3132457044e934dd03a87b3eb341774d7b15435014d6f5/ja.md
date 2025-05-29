```
tovrep(P::HPoly; [backend]=default_polyhedra_backend(P))
```

制約表現の多面体を頂点表現の多面体に変換します。

### 入力

  * `P`       – 制約表現の多面体
  * `backend` – （オプション、デフォルト: `default_polyhedra_backend(P)`）多面体計算のためのバックエンド

### 出力

制約表現の与えられた多面体の頂点表現である `VPolytope`。

### 注意事項

変換は数値型を保持しない場合があります（例: `N == Float32`）、バックエンドによって異なります。サポートされているバックエンドの詳細については[Polyhedraのドキュメント](https://juliapolyhedra.github.io/)を参照してください。
