```
svdsketch(A[, tol]; [maxrank, blocksize, maxiter, poweriter]) -> (U, S, V, apxerror)
```

行列 $A$ の低ランク行列スケッチの特異値分解 (SVD) を返します。行列スケッチは、$A$ の最も重要な特徴のみを反映し（許容誤差まで）、`svds` を使用するよりも大きな行列の SVD の計算を高速化します。

$$
A
$$

のスケッチは、$\|U \Sigma V^T - A\|_F / \|A\|_F \leq \text{tol}$ を満たします。`tol` のデフォルト値は `eps(eltype(A))^(1/4)` です。

SVD に加えて、ベクトル `apxerror` が返され、そのエントリは各イテレーションにおける相対近似誤差を表します。$\|U \Sigma V^T - A\|_F / \|A\|_F$。`apxerror` の長さはイテレーションの回数に等しく、`apxerror[end]` は出力の相対近似誤差です。

# オプション

`maxrank`: 行列スケッチのランクは `maxrank` を超えません。デフォルト値は `minimum(size(A))` です。

`blocksize`: 大きな値は必要なイテレーションの数を減少させますが、収束を達成するために必要以上に高いランクの結果をもたらす可能性もあります。デフォルト値は `min(max(floor(Integer, 0.1*size(A, 1)), 5), maxrank)` です。

`maxiter`: アルゴリズムの最大イテレーション数。デフォルト値は `maxrank ÷ blocksize` です。

`poweriter`: アルゴリズムの各イテレーション内で実行されるパワーイテレーションの数。パワーイテレーションは $U$ と $V$ の出力の直交性を改善します。デフォルト値は 1 です。
