```
low_connectivity([rng], [T], dims...;
                 return_sparse = false, connected=false,
                 in_degree = 1, radius = 1.0, cut_cycle = false)
```

内部リザーバ接続行列を低接続性で構築します。

この関数は、各ノードの指定された入次数を持つ正方形のリザーバ行列を作成します [^griffith2019]。`in_degree` が 1 の場合、`connected` が `true` のときに完全に接続されたサイクルを強制できます。それ以外の場合は、ランダムな接続パターンを生成します。

# 引数

  * `rng`: 擬似乱数生成器。デフォルトは WeightInitializers の `Utils.default_rng()` です。
  * `T`: リザーバ行列の要素の型。デフォルトは `Float32` です。
  * `dims`: リザーバ行列の次元。

# キーワード引数

  * `return_sparse`: `true` の場合、関数はリザーバ行列を疎行列として返します。デフォルトは `false` です。
  * `connected`: `in_degree == 1` の場合、`true` のときに接続されたサイクルが強制されます。デフォルトは `false` です。
  * `in_degree`: 各ノードの入ってくる接続の数。ノードの数を超えてはいけません。デフォルトは 1 です。
  * `radius`: リザーバの望ましいスペクトル半径。デフォルトは 1.0 です。
  * `cut_cycle`: `true` の場合、サイクルから1つのエッジを削除して切断します。デフォルトは `false` です。

[^griffith2019]: Griffith, Aaron, Andrew Pomerance, and Daniel J. Gauthier. "Forecasting chaotic systems with very low connectivity reservoir computers." Chaos: An Interdisciplinary Journal of Nonlinear Science 29.12 (2019).
