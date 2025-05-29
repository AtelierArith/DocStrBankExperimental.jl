```
defVars(dimNames, dimTypes; <keyword arguments>)
```

特定の次元とタイプを持つ空の NDSparse IndexedTable を定義します。

# 引数

  * `dimNames`: 定義する次元の名前の配列
  * `dimTypes`: 次元のタイプの配列
  * `valueType` (デフォルト: `Float64`): テーブルの値列のタイプ
  * `n` (デフォルト=`1`): 指定されたテーブルのコピーの数を返します（複数の変数を一度に定義するのに便利です。この場合、タプルが返されます）

# # 例

# ```julia

# julia> price,demand,supply = defVars(["region","item","class"],[String,String,Int64],valueType=Float64,n=3 )

# julia> waterContent = defVars(["region","item"],[String,String])

# julia> price["US","apple",1] = 3.2

# julia> waterContent["US","apple"] = 0.2

# ```

# 
