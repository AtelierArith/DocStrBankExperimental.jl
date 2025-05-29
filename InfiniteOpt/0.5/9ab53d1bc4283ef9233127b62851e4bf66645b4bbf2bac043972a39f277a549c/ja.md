```
derivative_method(dref::DerivativeRef)::AbstractDerivativeMethod
```

`dref`によって使用される評価方法を返します。これは、導関数を評価するために使用される数値計算スキームを決定します。これは、導関数が定義される無限のパラメータに関して設定されていることに注意してください。

**例**

```julia-repl
julia> derivative_method(dref) 
FiniteDifference(Backward, true)
```
