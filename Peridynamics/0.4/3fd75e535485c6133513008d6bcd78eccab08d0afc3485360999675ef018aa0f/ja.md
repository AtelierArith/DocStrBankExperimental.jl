```
@mpiroot [option] expression
```

コードはMPIランクがゼロの場合に実行されます。次のようなものに変わります：

```julia
if mpi_isroot()
    expression
end
```

# オプション

  * `:wait`: すべてのMPIランクは、ルートランクが`expression`の評価を終えるまで待機します。

参照：[`mpi_isroot`](@ref)。
