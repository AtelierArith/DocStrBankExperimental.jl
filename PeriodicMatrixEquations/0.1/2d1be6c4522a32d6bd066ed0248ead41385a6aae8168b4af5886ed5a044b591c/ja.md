```
pdlyap(A, C; adj = true, stability_check = false) -> X
```

周期的離散時間リャプノフ方程式を解きます。

```
A'σXA + C = X  for adj = true
```

または 

```
AXA' + C = σX  for adj = false,
```

ここで `σ` は前方シフト演算子 `σX(i) = X(i+1)` です。

周期行列 `A` と `C` は同じ型、同じ次元、かつ整合的な周期を持つ必要があり、さらに `C` は対称でなければなりません。得られる対称的な周期解 `X` は `A` と `C` の最小公倍数の整合的な周期に設定され、サブ周期の数はそれに応じて調整されます。

`stability_check = true` の場合、`A` の特性乗数の安定性がチェックされ、特性乗数のいずれかが絶対値1以上である場合はエラーが発生します。

周期行列 `A` の周期的シュール形式に基づくバーテルス-スチュワート法の周期的離散アナログが使用されます [1]。

*参考文献:*

[1] A. Varga. Periodic Lyapunov equations: some applications and new algorithms.                Int. J. Control, vol, 67, pp, 69-87, 1997.
