```
OrthogonalCollocation{Q <: MeasureToolbox.AbstractUnivariateMethod
                      } <: GenerativeDerivativeMethod
```

A `DataType` for storing information about orthogonal collocation over finite  elements to approximate derivatives. The constructor is of the form:

```
    OrthogonalCollocation(num_nodes::Int, 
                          [quad::AbstractUnivariateMethod = GaussLobatto])
```

**Fields**

  * `num_nodes::Int`: The number of collocation points (nodes) per finite element.
  * `quadrature_method::Q`: The quadrature method uses to choose the collocation points.
