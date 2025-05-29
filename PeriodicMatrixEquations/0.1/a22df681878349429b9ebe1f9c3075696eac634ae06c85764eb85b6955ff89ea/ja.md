```
pslyapd(A, C; adj = true, stability_check = false) -> X
```

周期的離散時間リャプノフ方程式を解きます。

平方の `n` 次の周期行列 `A(i)`, `i = 1, ..., pa` と `C(i)`, `i = 1, ..., pc` の周期 `pa` と `pc` に対して、周期 `p = lcm(pa,pc)` の周期的リャプノフ方程式の周期的解 `X(i)`, `i = 1, ..., p` が計算されます：

```
A(i)'*X(i+1)*A(i) + C(i) = X(i), i = 1, ..., p     for `adj = true`; 

A(i)*X(i)*A(i)' + C(i) = X(i+1), i = 1, ..., p     for `adj = false`.
```

周期行列 `A` と `C` はそれぞれ `n×n×pa` および `n×n×pc` の3次元配列 `A` と `C` に格納され、`X` は `n×n×p` の3次元配列として結果が得られます。

また、周期行列 `A` と `C` はそれぞれ `pa` 次元および `pc` 次元の行列ベクトル `A` と `C` に格納され、`X` は `p` 次元の行列ベクトルとして結果が得られます。

`stability_check = true` の場合、`A` の特性乗数の安定性がチェックされ、特性乗数のいずれかが1以上の絶対値を持つ場合はエラーが発生します。

周期行列 `A` の周期的シュール形式に基づくバーテルス-スチュワート法の周期的離散アナログが使用されます [1]。

*参考文献:*

[1] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
