```
simplot(sys, data, x0=:estimate; ploty=true, plote=false, sysname="")
```

システムシミュレーションと測定出力をプロットして比較します。

デフォルトでは、初期条件 `x0` はデータを使用して推定されます。シミュレーションを原点から開始するには、`x0 = :zero` または `x0 = zeros(sys.nx)` を指定してください。

  * `ploty` は測定信号をプロットするかどうかを決定します
  * `plote` は残差をプロットするかどうかを決定します
