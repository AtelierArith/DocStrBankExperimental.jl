```
arrays(collection)
```

データフレームのエントリの画像の配列のためのジェネレーター。

`collection`を各`path`と`hdu`を使用して反復し、データを`Array`にロードします。

# 例

```julia
collection = fitscollection("~/data/tekdata")
data = arrays(collection) |> collect
```

これにより、`collection`に存在するすべての画像配列が返されます。これはforループを介しても使用できます。

```julia
collection = fitscollection("~/data/tekdata")
for arr in arrays(collection)
    @assert arr isa Array
    println(size(arr))
end

# 出力
(1048, 1068)
(1048, 1068)
...
```
