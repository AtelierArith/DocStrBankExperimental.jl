```
defVars(size; <キーワード引数>)
```

特定の次元と型を持つ多次元配列を定義し、すべて`missing`値で埋めます。

# 引数

  * `size`: 必要な次元のタプル
  * `valueType` (デフォルト: `Float64`): 必要な配列の内部型
  * `n` (デフォルト=`1`): 指定されたテーブルのコピー数を返します（複数の変数を一度に定義するのに便利です。この場合、タプルが返されます）
  * `missingValue` (デフォルト=`missing`): 行列を埋める方法

# # 例

# ```julia

# julia> price,demand,supply = defVars((3,4,5),valueType=Float64,n=3 )

# julia> waterContent = defVars((3,4))

# julia> price[2,3,1] = 3.2

# julia> waterContent[2,3] = 0.2

# ```

```
