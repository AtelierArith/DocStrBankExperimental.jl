```
Dictionary(inds, values)
Dictionary{I}(inds, values)
Dictionary{I, T}(inds, values)
```

2つの反復可能な入力 `inds` と `values` からハッシュベースの辞書を構築します。`inds` の最初の値は `values` の最初の値のインデックスになります。入力はコピーされない場合があります。

注意: `inds` の値は一意でなければなりません。一意でない場合は `dictionary(zip(inds, values))` の使用を検討してください。`index` 関数も参照してください。

# 例

julia> Dictionary(["a", "b", "c"], [1, 2, 3]) 3-element Dictionary{String,Int64}  "a" │ 1  "b" │ 2  "c" │ 3

julia> Dictionary{String, Float64}(["a", "b", "c"], [1, 2, 3]) 3-element Dictionary{String,Float6464}  "a" │ 1.0  "b" │ 2.0  "c" │ 3.0 ```
