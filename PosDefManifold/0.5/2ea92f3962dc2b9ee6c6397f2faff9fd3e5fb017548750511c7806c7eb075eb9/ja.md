```
(1) spectralFunctions(P::ℍ{T}, func) where T<:RealOrComplex
(2) spectralFunctions(D::𝔻{S}, func) where S<:Real

(1) これは、このライブラリで実装されているすべての固有値のスペクトル関数の*母関数*です。これには以下が含まれます：

  * `pow`     (累乗),
  * `isqrt`   (逆平方根)。

関数`sqr`（平方）はこれを使用しません。なぜなら、単純な乗算によってより効率的に得られるからです。

標準パッケージ`LinearAlgebra`に実装されているもの以外の固有値のスペクトル関数が必要な場合は、この関数を使用できます。一般的には、直接呼び出すことはありません。

`func`は固有値に適用される関数です。

$P$はエルミート行列としてフラグを立てる必要があります。詳細は[typecasting matrices](@ref)を参照してください。`func`に応じて、正定値または半正定値の行列である必要があります。

実数の`Diagonal`行列（2）には特別なメソッドが提供されています。

!!! note "Nota Bene"
    関数`func`は`func.`構文をサポートする必要があり、したがって固有値に要素ごとに適用できる必要があります（これには[匿名関数](https://docs.julialang.org/en/v1/manual/functions/#man-anonymous-functions-1)が含まれます）。

### 数学

正定値行列$P$のスペクトル関数の定義は次のようになります：

$f\big(P\big)=Uf\big(Λ\big)U^H,$

ここで、$U$は$P$の固有ベクトルを列に持つ行列、$Λ$は対角にその固有値を持つ行列であり、$f$は固有値に要素ごとに適用される関数です。

**参照**: [`evd`](@ref)。

**例**

```

julia using LinearAlgebra, PosDefManifold n=5 P=randP(n) # P=randP(ComplexF64, 5)でエルミート複素行列を生成 noise=0.1; Q=spectralFunctions(P, x->x+noise) # 固有値にホワイトノイズを追加 tr(Q)-tr(P) ≈ noise*n ? println(" ⭐ ") : println(" ⛔ ") ```
