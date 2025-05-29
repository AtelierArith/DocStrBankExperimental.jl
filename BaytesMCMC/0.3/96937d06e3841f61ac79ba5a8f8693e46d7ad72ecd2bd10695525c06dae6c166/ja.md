```julia
sample_trajectory(_rng, trajectory, z, directions)

```

`z`から始まる`trajectory`をサンプリングし、`max_depth`まで進みます。`directions`は木の拡張方向を決定します。次の値を返します。

  * `ζ`: 木からの提案
  * `v`: 訪問したノードの統計
  * `termination`: `InvalidTree`（これは技術的には有効な木である最後の倍増ステップのターンを含みます）またはすべてのサブツリーが有効でターンが発生しない場合の`REACHED_MAX_DEPTH`
  * `depth`: サンプリングされた木の深さ。無効な隣接木につながる倍増ステップは`depth`に寄与しません。

# 例

```julia

```
