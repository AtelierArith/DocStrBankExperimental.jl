```
initial_condition_convergence_test(x, t, equations::BBMEquation1D, mesh)
```

周期的領域での収束テストに使用される移動波解で、ここでは次元変数に一般化されています。

（論文に誤りがあります：`cosh`の代わりに`sech^2`であるべきです）セクション4.1.3を参照してください：

  * Hendrik Ranocha, Dimitrios Mitsotakis and David I. Ketcheson (2020) A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
