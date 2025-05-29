```
OrthogonalCollocation{Q <: MeasureToolbox.AbstractUnivariateMethod
                      } <: GenerativeDerivativeMethod
```

有限要素上の直交コレクションに関する情報を格納するための`DataType`で、導関数を近似します。コンストラクタは次の形式です：

```
    OrthogonalCollocation(num_nodes::Int, 
                          [quad::AbstractUnivariateMethod = GaussLobatto])
```

**フィールド**

  * `num_nodes::Int`: 有限要素ごとのコレクションポイント（ノード）の数。
  * `quadrature_method::Q`: コレクションポイントを選択するために使用される数値積分法。
