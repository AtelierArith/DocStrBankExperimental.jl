```
work_precision_fixed(prob, algs, labels, dts, alg_ref;
                     compute_error = rel_max_error_tend,
                     seconds = 2,
                     numruns = 20)
```

作業精度図を作成するための辞書を返します。問題 `prob` は、`algs` にある各アルゴリズムによって、`dts` で定義されたすべてのステップサイズに対して解かれます。各ステップサイズについて、エラーと計算時間が辞書に保存されます。特定のステップサイズに対して解決が成功しなかった場合、辞書には `(Inf, Inf)` が保存されます。配列 `labels` にある文字列は、辞書のキーとして使用されます。エラー計算に使用される参照解は、アルゴリズム `alg_ref` を用いて計算されます。

### キーワード引数:

  * `compute_error(sol::ODESolution, ref_sol::ODESolution)`: `sol` と `ref_sol` の間のエラーを計算する関数。
  * `seconds`: 単一の解決の測定された計算時間が `seconds` より大きい場合、その計算時間が辞書に保存されます。
  * `numruns`: 単一の解決の測定された計算時間が `seconds` 以下の場合、`numruns` 回の解決が行われ、それぞれの計算時間の中央値が辞書に保存されます。
