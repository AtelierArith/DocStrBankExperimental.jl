```
@mpitime 式
```

mpiランクがゼロの場合に`式`の時間を計測します。次のように簡略化されます：

```julia
if mpi_isroot()
    @time 式
else
    式
end
```

参照：[`mpi_isroot`](@ref)。
