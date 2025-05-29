```
(1) function dim(X::AnyMatrix, [d])
(2) function dim(vector::AnyMatrixVector, [d])
(3) function dim(vector₂::AnyMatrixVector₂, [d])
```

(1) $X$ は実数または複素数の `Matrix`、`Diagonal`、`LowerTriangular` または `Hermitian` 行列です。 $X$ の次元を含む2タプルを返します。これは、`Matrix` 型を除くすべての可能な $X$ の型に対して同じ次元の2倍です。オプションで、次元（1または2）を指定して、その次元の長さだけを取得できます。

(2) `vector` は 𝕄Vector、𝔻Vector、𝕃Vector または ℍVector 型です（[AnyMatrixVector type](@ref)を参照）。保持している行列の数（次元1）とその次元（次元2および3）を含む3タプルを返します。オプションで、次元（1、2、または3）を指定して、その次元の長さだけを取得できます。

(3) `vector₂` は 𝕄Vector₂、𝔻Vector₂、𝕃Vector₂ または ℍVector₂ 型です（[AnyMatrixVector type](@ref)を参照）。次の内容を含む4タプルを返します。

  * 保持している行列のベクトルの数（次元1）、
  * 各行列のベクトルに含まれる行列の数を保持するベクトル（次元2）、
  * 行列の2つの次元（次元3および4）。

オプションで、次元（1、2、3、または4）を指定して、その次元の長さだけを取得できます。

`vector` と `vector₂` は [Array of Matrices types](@ref) です。記号 `ℍ`、`𝔻`、`𝕃` および `𝕄` のエイリアスについては [aliases](@ref) も参照してください。

!!! note "Nota Bene"
    次元を指定し、その範囲外である場合、関数はゼロを返します。

    `vector`(2) と `vector₂`(3) のオブジェクトは、同じ多様体に存在する行列を保持することを意図しているため、保持しているすべての行列が同じ次元であると仮定されます。行列の次元は次のように取得されます。

      * `vector`(2) の最初の行列、
      * `vector₂`(3) の最初のベクトルの最初の行列。


この関数は、行列ベクトルの次元を取得するために使用できないJuliaの [size](https://docs.julialang.org/en/v1/base/arrays/#Base.size) 関数を置き換えます。行列ベクトルのために `size` 関数をオーバーロードすることはできません。これは他のJulia関数に問題を引き起こすためです。

**例**

```julia
using LinearAlgebra, PosDefManifold
# (1)
M=randn(3, 4) # 3x4 の `Matrix` を生成
dim(M) # (3, 4) を返す
dim(M, 1) # 3 を返す
dim(M, 2) # 4 を返す
dim(M, 3) # 範囲外: 0 を返す

# (2)
Pset=randP(3, 4) # 4つの3x3 Hermitian 行列を保持する ℍVector を生成
dim(Pset) # (4, 3, 3) を返す
dim(Pset, 1) # 4 を返す
dim(Pset, 2) # 3 を返す
dim(Pset, 3) # 3 を返す

# (3)
# 4つのランダムな3x3 SPD行列のセットを生成
Pset=randP(3, 4)
# 40のランダムな4x4 SPD行列のセットを生成
Qset=randP(3, 40)
A=ℍVector₂([Pset, Qset])
dim(A) # (2, [4, 40], 3, 3) を返す
dim(A, 1) # 2 を返す
dim(A, 2) # [4, 40] を返す
dim(A, 2)[1] # 4 を返す
dim(A, 3) # 3 を返す
dim(A, 4) # 3 を返す
dim(A, 5) # 範囲外: 0 を返す

# 注意: k 個の ℍVector オブジェクトを保持する ℍVector₂ オブジェクトを作成するには
sets=ℍVector₂(undef, k) # そしてそれらを埋めます
```
