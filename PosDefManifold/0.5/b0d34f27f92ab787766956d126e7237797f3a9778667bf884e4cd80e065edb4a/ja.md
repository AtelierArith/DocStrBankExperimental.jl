```
fDiag(func::Function, X::AnyMatrix, k::Int=0)
```

**エイリアス**: `𝑓𝔻`

関数 `func` を実数または複素数の `Diagonal`、`LowerTriangular`、`Matrix` または `Hermitian` 行列 $X$ の $k^{th}$ 対角要素に要素ごとに適用し、これらの要素を持つ対角行列を返します。 $X$ はすべての場合において正方行列でなければなりませんが、𝕄=`Matrix` 型の引数の場合は、次元が *r⋅c* で *r ≠ c* である可能性があります。

対角の番号付けについては、julia の [tril(M, k::Integer)](https://bit.ly/2Tbx8o7) 関数を参照してください。

デフォルトでは主対角線が考慮されます。

  * $$
    X
    $$

    が `Diagonal` の場合、$k$ は自動的にゼロ（主対角線）に設定されます。
  * $$
    X
    $$

    が `LowerTriangular` の場合、$k$ は正の値にはできません。

$$
X
$$

が長方形の場合、結果の次元は $X$ のサイズと選択した対角線に依存します。例えば、

  * *r ≠ c* かつ $k$=0（主対角線）の場合、結果の次元は min*(r,c)*⋅*min(r,c)* になります。
  * $$
    X
    $$

    *3⋅4* かつ $k=-1$ の場合、結果は *2⋅2* になります。
  * $$
    X
    $$

    *3⋅4* かつ $k=1$ の場合、結果は *3⋅3* になります。など。

!!! note "Nota Bene"
    関数 `func` は `func.` 構文をサポートする必要があり、したがって選択した対角線の要素に要素ごとに適用できる必要があります（これには [匿名関数](https://docs.julialang.org/en/v1/manual/functions/#man-anonymous-functions-1) が含まれます）。入力行列が複素数の場合、関数 `func` は複素数の引数をサポートできる必要があります。


**関連項目**: [`DiagOfProd`](@ref), [`tr`](@ref).

**例**

```julia
using PosDefManifold
P=randP(5) # Hermitian 行列を生成するには P=randP(ComplexF64, 5) を使用

# P の最初の下対角線の逆数を持つ対角行列
D=fDiag(inv, P, -1)

(Λ, U) = evd(P) # Λ は P の固有値を保持します。evd を参照

# 固有値の対数を持つ対角行列
Δ=fDiag(log, Λ)

# 固有値の二乗のための匿名関数を使用
Δ=fDiag(x->x^2, Λ)
```
