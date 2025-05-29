```
check_gradient(M, F, gradF, p=rand(M), X=rand(M; vector_at=p); kwargs...)
```

数値的に、`F(M,p)`の勾配`gradF(M,p)`が正しいかどうかを検証します。つまり、

$$
f(\operatorname{retr}_p(tX)) = f(p) + t⟨\operatorname{grad} f(p), X⟩ + \mathcal O(t^2)
$$

ということです。言い換えれば、関数$f$とその一次テイラー展開の間の誤差が$\mathcal O(t^2)$の範囲で振る舞うことを示し、これにより勾配が正しいことを示します。詳細は[Boumal:2023; Section 4.8](@cite)も参照してください。

誤差が指定された許容範囲を下回り、かつ手法が正確であれば、プロットは生成されません。

# キーワード引数

  * `check_vector`:      (`true`) $\operatorname{grad} f(p) ∈ T_p\mathcal M$であることを`is_vector`を使用して検証します。
  * `exactness_tol`:     (`1e-12`) すべての誤差がこの許容範囲を下回る場合、勾配は正確であると見なされます。
  * `io`:                (`nothing`) 結果を出力するための`IO`を提供します。
  * `gradient`:          (`grad_f(M, p)`) 勾配関数の代わりに、`p`での勾配を直接提供することもできます。
  * `limits`:            (`(1e-8,1)`) `log_range`内の制限を指定します。
  * `log_range`:         (`range(limits[1], limits[2]; length=N)`) - 勾配線をサンプリングするためのポイントの範囲（対数スケール）を指定します。
  * `N`:                 (`101`) `log_range`のデフォルト範囲$[10^{-8},10^{0}]$内で検証するポイントの数です。
  * `plot`:              (`false`) 結果をプロットするかどうか（`Plots.jl`がロードされている場合）。プロットは対数-対数スケールです。これは返され、保存することもできます。
  * `retraction_method`: (`default_retraction_method(M, typeof(p))`) 使用する後退法です。
  * `slope_tol`:         (`0.1`) 近似の傾き（全体）の許容範囲です。
  * `atol`, `rtol`:      (`isapprox`と同じデフォルト) `check_vector`が`true`に設定されている場合、`is_vector`に渡される許容範囲です。
  * `error`:             (`:none`) エラーの処理方法、可能な値: `:error`, `:info`, `:warn`
  * `window`:            (`nothing`) 傾き推定に使用される`log_range`内のウィンドウサイズを指定します。デフォルトは、すべてのウィンドウサイズ`2:N`を使用します。

残りのキーワード引数は`check_vector`呼び出しにも渡されるため、許容範囲を簡単に設定できます。
