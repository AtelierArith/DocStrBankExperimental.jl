```
Gval = evalfr(sys; fval = 0, atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true)
```

記述子システム `sys = (A-λE,B,C,D)` に対して、伝達関数行列 `G(λ)` の値 `Gval` を評価します。ここで、`G(λ) = C*inv(λE-A)*B+D` の `λ = val` のときの値であり、連続時間システムの場合は `val = im*fval`、離散時間システムの場合は `val = exp(im*fval*sys.Ts)` です。計算された `Gval` は、`val` が `G(λ)` の極（有限または無限）である場合、無限のエントリを持ちます。`val` が有限であり、`val*E-A` が特異であるか、または `val = Inf` で `E` が特異である場合、`Gval` のエントリは各入力-出力チャネルの最小実現に対して別々に評価されます。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ行列 `A`、`B`、`C`、`D` の非ゼロ要素に対する絶対許容誤差、行列 `E` の非ゼロ要素に対する絶対許容誤差、そして行列 `A`、`B`、`C`、`D` および `E` の非ゼロ要素に対する相対許容誤差を指定します。キーワード引数 `atol` は、`atol1 = atol` および `atol2 = atol` を同時に設定するために使用できます。

個々の入力-出力チャネルの最小実現の計算は、ペンシル操作アルゴリズムに依存しており、これは `fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解、またはSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算コストは高くなります。
