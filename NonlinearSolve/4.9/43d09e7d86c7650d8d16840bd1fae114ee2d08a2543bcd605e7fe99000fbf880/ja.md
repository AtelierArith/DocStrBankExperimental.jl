```
FastLevenbergMarquardtJL(
    linsolve::Symbol = :cholesky;
    factor = 1e-6, factoraccept = 13.0, factorreject = 3.0, factorupdate = :marquardt,
    minscale = 1e-12, maxscale = 1e16, minfactor = 1e-28, maxfactor = 1e32,
    autodiff = nothing
)
```

`NonlinearLeastSquaresProblem`を解くための[FastLevenbergMarquardt.jl](https://github.com/kamesy/FastLevenbergMarquardt.jl)のラッパーです。他のキーワード引数の詳細については、`FastLevenbergMarquardt.jl`のドキュメントを参照してください。

### 引数

  * `linsolve`: 使用する線形ソルバー。`:qr`または`:cholesky`を指定できます。

### キーワード引数

  * `autodiff`: ヤコビ行列に使用されるバックエンドを決定します。この引数は、解析的ヤコビ行列が渡された場合は無視され、その代わりに使用されることに注意してください。デフォルトは`nothing`で、これは問題の仕様に応じてデフォルトが選択されることを意味します！

!!! note
    このアルゴリズムは、`FastLevenbergMarquardt.jl`がインストールされ、ロードされている場合にのみ利用可能です。

