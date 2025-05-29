```
sigmaplot(sys, args...; hz=false balance=true, extrema)
sigmaplot(LTISystem[sys1, sys2...], args...; hz=false, balance=true, extrema)
```

`LTISystem`(s)の周波数応答の特異値をプロットします。周波数ベクトル `w` をオプションで提供できます。

  * `hz=true` の場合、プロットのx軸はヘルツで表示され、入力周波数ベクトルは依然としてrad/sとして扱われます。
  * `balance`: プロットする前にシステムに対して[`balance_statespace`](@ref)を呼び出します。
  * `extrema`: 最も大きい特異値と最も小さい特異値のみをプロットします。

`kwargs`はPlots.plotへの引数として送信されます。
