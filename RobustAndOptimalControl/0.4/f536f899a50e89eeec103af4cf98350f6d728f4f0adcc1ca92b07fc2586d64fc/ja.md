```
specificationplot([S,CS,T], [WS,WU,WT])
```

この関数は、制御合成を視覚化します。これは、三つの重み関数 $W_S(s), W_U(s), W_T(s)$ を逆転させてスケーリングしたものを γ で、対応する伝達関数 $S(s), C(s)S(s), T(s)$ と比較して、仕様が満たされていることを視覚的に確認するために [`hinfsynthesize`](@ref) を使用します。これは、MIMO および SISO システムの両方で実行できます。

# キーワード引数

  * `wint`: `(-3, 5)` 周波数範囲 (log10)
  * `wnum`: 201 周波数点の数
  * `hz`: true
  * `nsigma`: typemax(Int) 表示する特異値の数
  * `s_labels`: `[   "σ(S)",   "σ(CS)",   "σ(T)",

]`

  * `w_labels`: `[   "γ σ(Wₛ⁻¹)",   "γ σ(Wᵤ⁻¹)",   "γ σ(Wₜ⁻¹)",

]`

  * `colors`: `[:blue, :red, :green]` $S$, $CS$ および $T$ の色
