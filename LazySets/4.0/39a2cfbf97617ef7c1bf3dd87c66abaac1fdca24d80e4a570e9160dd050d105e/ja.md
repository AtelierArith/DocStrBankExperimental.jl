```
minkowski_difference(P::LazySet, Q::LazySet)
```

多面体集合とコンパクト集合の具体的なミンコフスキー差（幾何学的差）。

### 入力

  * `P` – 多面体集合
  * `Q` – `P` から引かれるコンパクト集合

### 出力

`P` が有界であれば `P` から `Q` を引いたミンコフスキー差に対応する `HPolytope` を返し、`P` が無限大であれば `HPolyhedron` を返します。

### 注意事項

この実装は、集合 `P` が多面体であり、集合 `Q` が有界であることを要求します。

### アルゴリズム

このメソッドは [KolmanovskyG98; Theorem 2.3](@citet) を実装しています：

仮定 $P$ は多面体である

$$
P = \{z ∈ ℝ^n: sᵢᵀz ≤ rᵢ,~i = 1, …, k\}.
$$

ここで $sᵢ ∈ ℝ^n, sᵢ ≠ 0$、および $rᵢ ∈ ℝ$ とします。$ρ(sᵢ,Q)$ が $i = 1, …, k$ に対して定義されていると仮定します。すると、ミンコフスキー差は

$$
\{z ∈ ℝ^n: sᵢᵀz ≤ rᵢ - ρ(sᵢ,Q),~i = 1, …, k\}.
$$

アルゴリズムは `Q` にサポート関数を適用しますが、`P` が凸である限り、$P ⊖ Q = P ⊖ \text{CH}(Q)$ となります。ここで CH は凸包を示します。したがって、`Q` が型情報によって凸でない場合、遅延 `ConvexHull` でラップします。 ```
