```
FileProduct(path, varname::Symbol, dir_path = nothing)
```

[`FileProduct`](@ref)を宣言し、`Prefix`のルートに対して相対的に位置するファイルを指します。満たされるためには単に存在する必要があります。最初の引数`path`は、単一の`AbstractString`または複数のパスをチェックできるようにする`Vector{String}`です。
