```
cartesian_product(X::LazySet, Y::LazySet; [backend]=nothing,
                  [algorithm]::String="vrep")
```

2つの集合の直積を計算します。

### 入力

  * `X`         – 集合
  * `Y`         – 集合
  * `backend`   – （オプション、デフォルト: `nothing`）多面体計算のためのバックエンド
  * `algorithm` – （オプション、デフォルト: "hrep"）集合 `X` と `Y` を直積を取る前に変換するために使用される方法；次の中から選択：

      * "vrep"（頂点表現を使用）
      * "hrep"（制約表現を使用）
      * "hrep_polyhedra"（制約表現と `Polyhedra` を使用）

### 出力

`X` と `Y` の具体的な直積から得られる `VPolytope`（"vrep" が使用された場合）または `HPolytope`/`HPolyhedron`（"hrep" または "hrep_polyhedra" が使用された場合）。`HPolytope` と `HPolyhedron` の選択は、型から推測される有界性情報に基づいて行われます。

### 注意事項

サポートされているバックエンドに関する詳細は [Polyhedraのドキュメント](https://juliapolyhedra.github.io/) を参照してください。

`X` を1次元の区間に変換でき、`Y` の頂点が利用可能な場合は、`algorithm="vrep"` を使用してください。
