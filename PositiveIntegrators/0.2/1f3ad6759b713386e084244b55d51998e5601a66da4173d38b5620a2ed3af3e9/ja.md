```
work_precision_adaptive(prob, algs, labels, abstols, reltols, alg_ref;
                        adaptive_ref = false,
                        abstol_ref = 1e-14,
                        reltol_ref = 1e-13,
                        compute_error = rel_max_error_tend,
                        seconds = 2,
                        numruns = 20,
                        kwargs...)
```

作業精度図を作成するための辞書を返します。問題 `prob` は、`algs` に定義された各アルゴリズムによって、`abstols` および `reltols` に定義されたすべての許容誤差で解かれます。それぞれの許容誤差に対して、誤差と計算時間が辞書に保存されます。指定された許容誤差で解決が成功しなかった場合、辞書には `(Inf, Inf)` が保存されます。配列 `labels` の文字列は、辞書のキーとして使用されます。誤差計算に使用される参照解は、アルゴリズム `alg_ref` で計算されます。追加のキーワード引数は `solve` に渡されます。

### キーワード引数:

  * `adaptive_ref`: `true` の場合、参照解は許容誤差 `abstol_ref` と `reltol_ref` で適応的に計算されます。そうでない場合は $10^5$ ステップが使用されます。
  * `abstol_ref`: `adaptive_ref` を参照してください。
  * `reltol_ref`: `adaptive_ref` を参照してください。
  * `compute_error(sol::ODESolution, ref_sol::ODESolution)`: `sol` と `ref_sol` の間の誤差を計算する関数です。
  * `seconds`: 単一の解法の測定された計算時間が `seconds` より大きい場合、この計算時間が辞書に保存されます。
  * `numruns`: 単一の解法の測定された計算時間が `seconds` 以下の場合、`numruns` 回の解法が実行され、各計算時間の中央値が辞書に保存されます。
