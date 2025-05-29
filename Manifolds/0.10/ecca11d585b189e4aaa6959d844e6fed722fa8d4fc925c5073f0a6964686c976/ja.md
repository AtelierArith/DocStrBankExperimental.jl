```
Random.rand!(
    rng::AbstractRNG,
    M::MultinomialSymmetricPositiveDefinite,
    p::AbstractMatrix,
)
```

[`MultinomialSymmetricPositiveDefinite`](@ref) 多様体上のランダム点を生成します。手順は以下の通りです：

1. ランダムな [完全正行列](https://en.wikipedia.org/wiki/Totally_positive_matrix) を生成します。 a. `n` 個のランダムな正の増加実数からなるベクトル `L` を構築します。 b. シーケンス `L` に基づいて [バンダーモンド行列](https://en.wikipedia.org/wiki/Vandermonde_matrix) `V` を構築します。 c. L および U 成分の両方が正の要素を持つように `V` の LU 因数分解を行います。 d. U の対角成分を取り、U をそれで割ることによって LU 因数分解を LDU 因数分解に変換します、`V=LDU`。 e. 完全正である新しい行列 `R = UDL` を構築します。
2. 完全正行列 `R` を [`MultinomialDoubleStochastic`](@ref) 行列の多様体に射影します。
3. 射影された行列を対称化し、結果を返します。

この方法は、https://math.stackexchange.com/questions/2773460/how-to-generate-a-totally-positive-matrix-randomly-using-software-like-maple に記載されている手順に大まかに従っています。
