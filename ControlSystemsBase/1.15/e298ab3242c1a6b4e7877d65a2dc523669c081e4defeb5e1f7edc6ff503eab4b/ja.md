```
rgaplot(sys, args...; hz=false)
rgaplot(LTISystem[sys1, sys2...], args...; hz=false, balance=true)
```

`LTISystem`(s)の相対ゲイン配列のエントリをプロットします。周波数ベクトル `w` をオプションで提供できます。

  * `hz=true` の場合、プロットのx軸はヘルツで表示され、入力周波数ベクトルは依然としてrad/sとして扱われます。
  * `balance`: プロットする前にシステムに対して [`balance_statespace`](@ref) を呼び出します。

`kwargs` は `Plots.plot` への引数として送信されます。
