```
getraster(T::Type{CHELSA{Climate}}, [layer::Union{Tuple,Symbol}]; month) => Vector{String}
```

[`CHELSA`](@ref) [`Climate`](@ref) データをダウンロードします。

# 引数

  * `layer` `Symbol` または `Symbol` の `Tuple` で、`(:clt, :cmi, :hurs, :ncdf, :pet, :pr, :rsds, :sfcWind, :tas, :tasmax, :tasmin, :vpd)` から選択します。

# キーワード

  * `month`: `Integer` または `Integer` の `AbstractArray`。`1:12` から選択します。

ダウンロードされたファイルまたは既存のファイルのファイルパスを返します。
