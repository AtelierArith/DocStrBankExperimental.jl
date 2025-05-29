```
(1) normalizeCol!(X::𝕄{T}, j::Int)
(2) normalizeCol!(X::𝕄{T}, j::Int, by::Number)
(3) normalizeCol!(X::𝕄{T}, range::UnitRange)
(4) normalizeCol!(X::𝕄{T}, range::UnitRange, by::Number)
上記すべて: ここで T<:RealOrComplex

実数または複素数要素からなる `Matrix` 型 $X$ に対して、

  * (1) $j^{th}$ 列を単位ノルムに正規化します
  * (2) $j^{th}$ 列の要素を数値 $by$ で割ります
  * (3) $range$ の列を単位ノルムに正規化します
  * (4) $range$ の列の要素を数値 $by$ で割ります。

$by$ は抽象スーパタイプ [Number](https://bit.ly/2JwXjGr) の数です。整数、実数、または複素数である必要があります。効率のために、$X$ の要素と同じ型であるべきです。

$range$ は [UnitRange](https://bit.ly/2HSfK5J) 型です。

メソッド (1) と (3) は、対象の列のノルムを計算するために [BLAS.nrm2](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BLAS.nrm2) ルーチンを呼び出します。 [Threads](@ref) を参照してください。

!!! note "Nota Bene"
    Julia は `Hermitian` 行列の列を正規化することを許可していません。この関数を `Hermitian` 行列に対して呼び出したい場合は、[行列の型変換](@ref) を参照してください。

**参照**: [norm](https://bit.ly/2TaAkR0) および以下の例については [randn](https://bit.ly/2I1Vgrg) を参照してください。

**関連**: [`colNorm`](@ref), [`colProd`](@ref).

**例**

```

julia using PosDefManifold X=randn(10, 20) normalizeCol!(X, 2)                  # (1) 列 2 を正規化 normalizeCol!(X, 2, 10.0)            # (2) 列 2 を 10.0 で割る normalizeCol!(X, 2:4)                # (3) 列 2 から 4 を正規化 X=randn(ComplexF64, 10, 20) normalizeCol!(X, 3)                  # (1) 列 3 を正規化 normalizeCol!(X, 3:6, (2.0 + 0.5im)) # (4) 列 3 から 5 を (2.0 + 0.5im) で割る ```
