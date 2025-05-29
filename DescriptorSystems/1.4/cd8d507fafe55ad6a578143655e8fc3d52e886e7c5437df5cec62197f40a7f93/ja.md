```
sys = dss(T, U, V, W; fast = true, contr = false, obs = false, minimal = false, atol = 0, rtol)
```

多項式行列 `T(λ)`, `U(λ)`, `V(λ)`, および `W(λ)` によって指定された多項式モデルに対して、入力-出力同等の記述子システム表現 `sys = (A-λE,B,C,D)` を構築します。ここで、

```
  V(λ)*inv(T(λ))*U(λ)+W(λ) = C*inv(λE-A)*B+D.
```

`minimal = true` の場合、得られる実現 `(A-λE,B,C,D)` は `A-λE` の最小の順序 `n` を持ちます。

`T(λ)`, `U(λ)`, `V(λ)`, および `W(λ)` は、`X(λ) = X_1 + λ X_2 + ... + λ**k X_(k+1)` の形の多項式行列として指定できます。ここで、`X = T`, `U`, `V`, `W` の場合、係数行列 `X_i`, `i = 1, ..., k+1` は 3 次元行列 `X` に格納され、`X[:,:,i]` には `λ**(i-1)` を掛けた `i` 番目の係数行列 `X_i` が含まれます。

`T(λ)`, `U(λ)`, `V(λ)`, および `W(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列、ベクトル、またはスカラーとしても指定できます。この場合、`T(λ)`, `U(λ)`, `V(λ)`, および `W(λ)` が同じ不確定量を持つかどうかのチェックは行われません。

計算された記述子実現は以下を満たします：

(1) `A-λE` は正則である；

(2) `rank[B A-λE] = n` （制御可能性）もし `minimal = true` または `contr = true` の場合；

(3) `rank[A-λE; C] = n` （可観測性）もし `minimal = true` または `obs = true` の場合；

(4) `A-λE` は `minimal = true` の場合、単純な無限固有値を持たない。

キーワード引数 `atol` と `rtol` は、それぞれ行列 `T(λ)`, `U(λ)`, `V(λ)`, および `W(λ)` の非ゼロ係数に対する絶対および相対許容誤差を指定します。デフォルトの相対許容誤差は `nt*ϵ` であり、ここで `nt` は正方行列 `T(λ)` のサイズで、`ϵ` はその係数の要素型の機械イプシロンです。

記述子実現は、[1] に記載された方法を使用して構築されます。

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).
