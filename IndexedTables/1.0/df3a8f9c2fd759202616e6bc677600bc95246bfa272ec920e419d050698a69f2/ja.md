```
dropmissing(t        )
dropmissing(t, select)
```

テーブル `t` の行を削除します。行には欠損値（`Missing` または `DataValue`）が含まれています。オプションで、`select` にある列のみを使用します。列の型は非欠損型に変換されます。例えば：

  * `Vector{Union{Int, Missing}}` -> `Vector{Int}`
  * `DataValueArray{Int}` -> Vector{Int}

# 例

```
t = table([0.1,0.5,missing,0.7], [2,missing,4,5], [missing,6,missing,7], names=[:t,:x,:y])
dropmissing(t)
dropmissing(t, (:t, :x))
```
