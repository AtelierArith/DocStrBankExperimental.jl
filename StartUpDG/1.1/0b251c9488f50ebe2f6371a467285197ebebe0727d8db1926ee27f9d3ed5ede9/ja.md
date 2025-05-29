```
MultidimensionalQuadrature
```

`Polynomial`の型パラメータで、特定の構造を持たないことを示します。使用例:

```julia
# これらは両方とも同等です
approximation_type = Polynomial{MultidimensionalQuadrature}() 
approximation_type = Polynomial(MultidimensionalQuadrature())
```
