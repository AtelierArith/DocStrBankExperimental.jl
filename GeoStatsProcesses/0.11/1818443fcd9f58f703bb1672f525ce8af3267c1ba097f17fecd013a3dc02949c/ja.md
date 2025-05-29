```
SEQSIM(; [options])
```

Gomez-Hernandezによって1993年に導入された逐次シミュレーション法。

この方法は、シミュレーション領域のすべての要素（すなわち、ジオメトリ）をパスに従って移動し、地質統計モデルを使用して隣接する要素のセットで条件付き分布を近似し、条件付き分布からサンプリングすることによって現在の要素に値を割り当てます。

## オプション

  * `path`         - シミュレーションパス（デフォルトは `LinearPath()`）
  * `minneighbors` - 最小隣接数（デフォルトは `1`）
  * `maxneighbors` - 最大隣接数（デフォルトは `26`）
  * `neighborhood` - 探索する隣接領域（デフォルトは `:range`）
  * `distance`     - 最近傍のための距離（デフォルトは `Euclidean()`）

条件付き分布は、`minneighbors` ≤ `n` ≤ `maxneighbors` となる隣接数 `n` に基づいて近似されます。

`neighborhood` は `MetricBall`、シンボル `:range` または `nothing` であることができます。シンボル `:range` は `MetricBall(range(f))` に変換され、ここで `f` は地質統計プロセスの地質統計関数です。`neighborhood` が `nothing` の場合、指定された `distance` に従って最近傍を見つけます。

## 参考文献

  * Gomez-Hernandez & Journel 1993. [Joint Sequential Simulation of MultiGaussian Fields](https://link.springer.com/chapter/10.1007/978-94-011-1739-5_8)

### 注意事項

この方法は隣接検索オプションとシミュレーションパスに非常に敏感です。基盤となる地質統計モデルで十分な隣接数が使用されるように注意が必要です。
