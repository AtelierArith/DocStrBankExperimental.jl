```
LeaveBallOut(ball; loss=Dict())
```

Leave-`ball`-out（別名：空間的leave-one-out）検証。オプションで、いくつかの変数に対する`LossFunctions.jl`からの`loss`関数を含む辞書を指定できます。

```
LeaveBallOut(radius; loss=Dict())
```

デフォルトでは、指定された`radius`のユークリッドボールを空間で使用します。

## 参考文献

  * Le Rest et al. 2014. [Spatial leave-one-out cross-validation for variable selection in the presence of spatial autocorrelation](https://onlinelibrary.wiley.com/doi/full/10.1111/geb.12161)
