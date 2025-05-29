```
struct CouplingModel{T}
    sites::Vector{Index{T}}
    terms::Vector{IDTensors}
end
```

`CouplingModel` は与えられた `OpStrings` ハミルトニアン項と `sites::Vector{Index}` のためのものです。

  * `sites::Vector{Index{T}}`: サイト `Index` 。
  * `terms::Vector{IDTensors}`: ハミルトニアン項のコレクション。
