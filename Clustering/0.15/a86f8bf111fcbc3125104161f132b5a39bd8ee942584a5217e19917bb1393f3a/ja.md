```
kmedoids(dist::AbstractMatrix, k::Integer; ...) -> KmedoidsResult
```

$$
n
$$

点を`k`クラスタにK-メドイドクラスタリングを実行します。`dist`行列（$n×n$、`dist[i, j]`は$j$-番目と$i$-番目の点の間の距離）を与えられます。

# 引数

  * `init`（デフォルトは`:kmpp`）：メドイドの初期化方法。以下のいずれかである可能性があります：

      * シードアルゴリズムの名前を示す`Symbol`（サポートされているメソッドのリストについては[Seeding](@ref Seeding)を参照）。
      * 初期メドイドとして使用する点のインデックスを提供する長さ`k`の整数ベクトル。
  * `maxiter`, `tol`, `display`：[共通オプション](@ref common_options)を参照

# 注意

この関数は*PAM*（メドイド周辺の分割）ではなく、*K-meansスタイル*のアルゴリズムを実装しています。K-meansスタイルのアルゴリズムは、より少ない反復で収束しますが、結果が悪化する（合計コストが10-20%高くなる）ことが示されています（例えば、[Schubert & Rousseeuw (2019)](@ref kmedoid_refs)を参照）。
