```
function GridEncoding(
    kab; n_dims::Int = 3, n_levels::Int = 16, scale::Float32 = 1.5f0,
    base_resolution::Int = 16, n_features::Int = 2, hashmap_size::Int = 19,
    align_corners::Bool = true, store_level_ids::Bool = false)
```

マルチ解像度ハッシュエンコーディング

# 引数:

  * `kab`: `GridEncoding`をインスタンス化するバックエンド。
  * `n_dims::Int`: 入力次元の数（例：3Dポイントの場合は3でなければならない）。
  * `n_levels::Int`: グリッド内のレベルの数。レベルの数が多いほど、デバイスメモリのコストを伴って精度が向上する。
  * `scale::Float32`: 各次のレベルのサイズをどれだけスケールするか。
  * `base_resolution::Int`: 初期解像度（1stレベル）。
  * `n_features::Int`: 各レベルの特徴のサイズ。
  * `hashmap_size::Int`: 一対一のマッピングからハッシュに切り替わるレベルのlog₂サイズ。
  * `align_corners::Bool`: `true`の場合、入力をそれぞれのレベル解像度にスケーリングする際にグリッドのコーナーを揃える。
  * `store_level_ids::Bool`: `true`の場合、`GridEncoding`は各特徴からグリッド内のそのレベルへのマッピングIDを保存する。これにより、`mean(scatter(mean, θ.^2, level_ids))`として`GridEncoding`パラメータの減衰を実装できる。インデックスはメモリ使用量を削減するために`Int8`型で保存される。

# 参考:

[https://nvlabs.github.io/instant-ngp/](https://nvlabs.github.io/instant-ngp/)
