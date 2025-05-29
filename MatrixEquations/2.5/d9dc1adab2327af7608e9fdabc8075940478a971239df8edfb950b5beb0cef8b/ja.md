```
X = tlyapc(A,C, isig = 1; fast = true, atol::Real=0, rtol::Real=atol>0 ? 0 : N*ϵ)
```

`isig = ±1` の場合に連続 T-Lyapunov 行列方程式の解を計算します。

```
            A*X + isig*transpose(X)*transpose(A) + C = 0
```

`A` のフルランク因子分解に基づく明示的な公式を使用します（[1] および [2] を参照）。 `A` と `C` はそれぞれ `m×n` および `m×m` 行列であり、`X` は `n×m` 行列です。行列 `C` は、`isig = 1` の場合は対称であり、`isig = -1` の場合は反対称でなければなりません。`atol` と `rtol` は、それぞれランク計算に使用される絶対および相対許容誤差です。デフォルトの相対許容誤差は `N*ϵ` であり、ここで `N = min(m,n)` で、ϵ は `A` の要素型の機械精度です。

`A` の基礎となるランクを明らかにする因子分解は、`fast = true`（デフォルト）の場合は列ピボットを伴う QR 因子分解であり、`fast = false` の場合はより信頼性の高い SVD 分解です。

[1] H. W. Braden. The equations A^T X ± X^T A = B. SIAM J. Matrix Anal. Appl., 20(2):295–302, 1998.

[2] C.-Y. Chiang, E. K.-W. Chu, W.-W. Lin, On the ★-Sylvester equation AX ± X^★ B^★ = C.     Applied Mathematics and Computation, 218:8393–8407, 2012.
