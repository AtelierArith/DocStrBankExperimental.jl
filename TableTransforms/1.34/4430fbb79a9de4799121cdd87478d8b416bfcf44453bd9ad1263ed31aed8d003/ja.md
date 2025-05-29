```
OneHot(col; categ=false)
```

カテゴリカル列 `col` を、CategoricalArrays.jl の `levels` 関数によって返されるレベルのワンホット列に変換します。`categ` オプションを使用すると、結果の列をブールベクトルではなくカテゴリカル配列に変換できます。

# 例

```julia
OneHot(1)
OneHot(:a)
OneHot("a")
OneHot("a", categ=true)
```
