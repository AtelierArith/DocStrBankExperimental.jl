```
describe(md; t = fill([(1, 0, 0)], nmodalities(md)), kwargs...)
```

`AbstractMultiDataset` の記述統計を新しい `DataFrame` の `Vector` として返します。各行は変数を表し、各列は要約統計量を表します。

# 引数

  * `md`: `AbstractMultiDataset`;
  * `t`: は `nmodalities` 要素のベクトルで、各要素は

```
i 番目のモダリティの次元と同じ長さのベクトルです。最も内側のベクトルの各要素は [`paa`](@ref) の引数のタプルです。
```

その他については [`DataFrames.describe`](@ref) 関数のドキュメントを参照してください。

# 例

TODO: 例
