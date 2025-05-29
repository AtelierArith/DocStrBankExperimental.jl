```
 FciqmcRunStrategy{T}
```

抽象型は、[`lomc!()`](@ref)の実行と終了のための戦略を表します。型パラメータ `T` は、シフトとノルムの報告に関連しています。

実装された戦略：

  * [`RunTillLastStep`](@ref)

!!! warning
    この戦略の使用は非推奨です。関連する引数を直接[`ProjectorMonteCarloProblem`](@ref)または[`lomc!()`](@ref)に渡してください。

