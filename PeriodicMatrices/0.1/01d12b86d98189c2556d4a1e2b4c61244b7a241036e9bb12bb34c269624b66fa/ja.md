```
pmderiv(A::PeriodicFunctionMatrix; h:Union{Real,Missing} = missing, method = "cd", discont = false) 
pmderiv(A::PeriodicTimeSeriesMatrix; h:Union{Real,Missing} = missing, method = "cd", discont = false) 
pmderiv(A::PeriodicSwitchingMatrix; h:Union{Real,Missing} = missing, method = "cd", discont = false)
```

連続時間周期行列の導関数を有限差分公式を使用して計算します。デフォルトでは `method = "cd"` であり、この場合、導関数の近似には中央差分公式が使用されます。 `method = "4d"` の場合、より高い精度のために4次有限差分公式が使用されます。 `method = ""` の場合、時間差 `h` が欠損しているか `h > 0` の場合は前方差分公式が使用され、`h < 0` の場合は後方差分公式が使用されます。 `discont = true` の場合、初期の不連続点 `t = 0` と終端の不連続点 `tsub := A.period/A.nperiod`（サブ期間）での不連続性は、`t = 0` および `t = tsub` でそれぞれ前方または後方の微分公式を使用することで回避されます。このアプローチは一般的に `t = 0` および `t = tsub` での精度の低い推定につながります。

*注:* `PeriodicTimeSeriesMatrix` および `PeriodicSwitchingMatrix` 型の周期行列に有限差分近似を適用できるようにするため、これらは `PeriodicFunctionMatrix` 型に変換されます。これらの表現の固有の不連続性のため、導関数の推定精度は通常低いです。精度を向上させるためには、`pmderiv` 関数を呼び出す前に、関数 [`ts2pfm`](@ref) によって提供されるスプラインベースの補間公式を使用してこれらの変換を行うことをお勧めします。
