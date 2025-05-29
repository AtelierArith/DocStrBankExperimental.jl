```
check_gradient(M, f, grad_f, p=rand(M), X=rand(M; vector_at=p); kwargs...)
```

関数 `f(M,p)` の勾配 `grad_f(M,p)` が正しいかどうかを数値的に検証します。つまり、

$$
f(\operatorname{retr}_p(tX)) = f(p) + t⟨\operatorname{grad} f(p), X⟩ + \mathcal O(t^2)
$$

ということです。言い換えれば、関数 $f$ とその一次テイラー展開との誤差が $\mathcal O(t^2)$ の挙動を示すことを確認します。これは勾配が正しいことを示します。詳細は[Boumal:2023; Section 4.8](@cite)も参照してください。

誤差が指定された許容範囲を下回り、かつ手法が正確である場合、プロットは生成されません。

# キーワード引数

  * `check_vector=true`: `is_vector`を使用して $\operatorname{grad}f(p) ∈ T_{p}\mathcal M$ を検証します。
  * `exactness_tol=1e-12`: すべての誤差がこの許容範囲を下回る場合、勾配は正確と見なされます。
  * `io=nothing`: 結果を出力するための `IO` を提供します。
  * `gradient=grad_f(M, p)`: 勾配関数の代わりに、`p` での勾配を直接提供できます。
  * `limits=(-8.0, 0.0)`: `log_range` の範囲を指定します。
  * `log_range=range(limits[1], limits[2]; length=N)`:

      * 勾配線をサンプリングするためのポイントの範囲（対数スケール）を指定します。
  * `N=101`: `log_range` のデフォルト範囲 $[10^{-8},10^{0}]$ 内で検証するポイントの数。
  * `plot=false`: 結果をプロットするかどうか（`Plots.jl` がロードされている場合）。プロットは対数-対数スケールです。これは返され、保存することもできます。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束 $\operatorname{retr}$、詳細は[再収束に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください。
  * `slope_tol=0.1`: 近似の傾き（グローバル）の許容範囲。
  * `atol`, `rtol`: （`isapprox` と同じデフォルト）`check_vector` が `true` に設定されている場合、`is_vector` に渡される許容範囲。
  * `error=:none`: エラーの処理方法、可能な値: `:error`, `:info`, `:warn`。
  * `window=nothing`: 傾き推定に使用される `log_range` 内のウィンドウサイズを指定します。デフォルトは、すべてのウィンドウサイズ `2:N` を使用します。

残りのキーワード引数も `check_vector` 呼び出しに渡されるため、許容範囲を簡単に設定できます。
