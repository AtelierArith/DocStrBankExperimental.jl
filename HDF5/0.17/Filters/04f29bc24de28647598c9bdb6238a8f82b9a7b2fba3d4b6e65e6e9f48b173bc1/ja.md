HDF5.Filters

このモジュールは、HDF5.jlでフィルターを使用するためのインターフェースを含んでいます。

# 使用例

```julia
using HDF5
using HDF5.Filters

# 新しいファイルを作成
fn = tempname()

# テストデータを作成
data = rand(1000, 1000)

# 書き込み用に一時ファイルを開く
f = h5open(fn, "w") 

# データセットを作成
dsdeflate = create_dataset(f, "deflate", datatype(data), dataspace(data),
                           chunk=(100, 100), deflate=3)

dsshufdef = create_dataset(f, "shufdef", datatype(data), dataspace(data),
                           chunk=(100, 100), shuffle=true, deflate=3)

dsfiltdef = create_dataset(f, "filtdef", datatype(data), dataspace(data),
                           chunk=(100, 100), filters=Filters.Deflate(3))

dsfiltshufdef = create_dataset(f, "filtshufdef", datatype(data), dataspace(data),
                               chunk=(100, 100), filters=[Filters.Shuffle(), Filters.Deflate(3)])

# データを書き込む
write(dsdeflate, data)
write(dsshufdef, data)
write(dsfiltdef, data)
write(dsfiltshufdef, data)

close(f)
```

## 追加の例

さらなる例については、[test/filter.jl](https://github.com/JuliaIO/HDF5.jl/blob/master/test/filter.jl)を参照してください。
