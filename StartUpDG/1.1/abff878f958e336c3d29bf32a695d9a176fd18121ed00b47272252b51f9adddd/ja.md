```
TensorProductQuadrature{T}
```

`Polynomial` に対する型パラメータで、数値積分がテンソル積構造を持つことを示します。使用例:

```julia
# これらはどちらも同等です
approximation_type = Polynomial{TensorProductQuadrature}(gauss_quad(0, 0, 1)) 
approximation_type = Polynomial(TensorProductQuadrature(gauss_quad(0, 0, 1)))
```
