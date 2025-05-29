```julia
    function load(filename::String)
```

ファイルに保存された `object` を読み込み、返します。ファイルのフルパスは `filename` として指定されます。

例えば、[`CVres`](@ref) 構造体や [`Pipeline`](@ref) タプルを読み込むために使用できます。

パイプラインに関しては、それが適用されるデータの次元と一致するかどうかのチェックは行われません。これはユーザーの責任です。

**参照** [`saveas`](@ref)
