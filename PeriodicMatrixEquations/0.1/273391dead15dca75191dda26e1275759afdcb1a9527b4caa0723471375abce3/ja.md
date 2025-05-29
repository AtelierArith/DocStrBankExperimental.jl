```
 pfdric(A, C, R, Q[, S]; itmax = 0, nodeflate = false, fast, rtol) -> (X, EVALS, F)
```

周期リカッティ差分方程式を解きます。

```
  X(i+1) = Q(i) + A(i)X(i)A(i)' - (A(i)X(i)C(i)' + S(i))*
                                 -1
           (C(i)X(i)C(i)' + R(i))  (A(i)X(i)C(i)' + S(i))'
```

安定化された周期カルマンゲインを計算します。

```
                                                       -1
  F(i) = -(C(i)X(i)A(i)' + S(i)')(C(i)X(i)C(i)' + R(i))
```

および `EVALS` における `A(i)-F(i)C(i)` の対応する安定なカルマンフィルタ特性乗数。

`n×n` および `m×n` の周期行列 `A(i)` と `C(i)` は `PeriodicArray` オブジェクト `A` と `C` に含まれており、同じサンプリング時間を持たなければなりません。 `R(i)`, `Q(i)` および `S(i)` は `A` と `C` と同じサンプリング時間を持つ `m×m`, `n×n` および `m×n` の周期行列であり、`R(i)` と `Q(i)` は対称でなければなりません。 `R`, `Q` および `S` は定数実行列として代わりに提供することもできます。 結果として得られる対称周期解 `X` とカルマンフィルタゲイン `F` は、`A`, `C`, `R` および `Q` の最小公倍数の周期に設定され、サブ周期の数はそれに応じて調整されます。

[1] の双対法が使用されます（キーワードパラメータの説明については [`prdric`](@ref) を参照してください）。

*参考文献*

[1] A. Varga. On solving periodic Riccati equations.       Numerical Linear Algebra with Applications, 15:809-835, 2008.
