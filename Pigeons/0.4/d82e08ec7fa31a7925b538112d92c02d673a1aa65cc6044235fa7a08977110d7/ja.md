```julia
pigeons(pt)

```

（パラレルテンパリングの一般化を）実行します。

これにより、各ラウンドの間に[`adapt()`](@ref)を介して適応を行いながら、[`run_one_round!()`](@ref)のいくつかのラウンドが呼び出されます。

また、ラウンドの間に[`report!()`](@ref)、[`write_checkpoint()`](@ref)、および[`run_checks()`](@ref)も呼び出されます。
