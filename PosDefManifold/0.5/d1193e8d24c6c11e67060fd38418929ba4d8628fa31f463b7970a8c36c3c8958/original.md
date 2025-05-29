```
(1) congruence(B::AnyMatrix, P::AnyMatrix, matrixType)
(2) congruence(B::AnyMatrix, 𝐏::AnyMatrixVector, matrixVectorType)
(3) congruence(B::AnyMatrix, 𝑷::AnyMatrixVector₂, matrixVector₂Type)
(4) congruence(𝐁::AnyMatrixVector, 𝑷::AnyMatrixVector₂, matrixVector₂Type)
```

**alias**: `cong`

(1) Return the congruent transformation

$BPB^H$,

for $B$ and $P$ any combination of `Hermitian`, `LowerTriangular`,  `Diagonal` or general `Matrix` type.

The result is of the `matrixType` argument, which must be provided and  must be one of these four abstract type (not an instance of them).  See [aliases](@ref) for shortening these type using symbols `ℍ`, `𝔻`, `𝕃` and `𝕄`.

(2) Return a vector of matrices holding the congruent transformations

$BP_kB^H$,

for all $k$ matrices in $𝐏={P_1,...,P_k}$, for $B$ and $𝐏$  any combination of matrix type `Hermitian`, `LowerTriangular`,  `Diagonal` or `Matrix` ($B$) and vector of matrices type `ℍVector`, `𝔻Vector`,  `𝕃Vector` and `𝕄Vector` ($𝐏$). See [Array of Matrices types](@ref).

The result is a vector of matrices of the `matrixVectorType` argument,  which must be provided and must be one of the following abstract types:  `ℍVector`, `𝔻Vector`, `𝕃Vector` or `𝕄Vector`  (and not an instance of these types).

(3) Return a vector of vector of matrices holding the  congruent transformations

$BP_{mk}B^H$,

for all $m$ vectors of $k[m]$ vectors of matrices in $𝑷$,  for $B$ and $𝑷$ any combination of matrix type `Hermitian`,  `LowerTriangular`, `Diagonal` or `Matrix` ($B$) and vector of matrices type  `ℍVector₂`, `𝔻Vector₂`,  `𝕃Vector₂` and `𝕄Vector₂` ($𝑷$). See [Array of Matrices types](@ref).

The result is a vector of vector of matrices of the `matrixVector₂Type`  argument, which must be provided and must be one of the following  abstract types: `ℍVector₂`, `𝔻Vector₂`, `𝕃Vector₂` or `𝕄Vector₂`  (and not an instance of these types).

(4) Return a vector of vector of matrices holding the  congruent transformations

$B_iP_{ij}B_j^H$, for $i,j∈[1,...,m]$.

for $𝐁$ holding $m$ matrices and $𝑷$ holding $m$ vectors  holding $m$ matrices each.  Note that, differently from method (3), here the vectors of $𝑷$  are all of the same length and this is eaxctly the length of $𝐁$.  $𝐁$ and $𝑷$ may be any combination of matrix vector type `ℍVector`,  `𝔻Vector`, `𝕃Vector` and `𝕄Vector` ($𝐁$) and vector of matrices type  `ℍVector₂`, `𝔻Vector₂`, `𝕃Vector₂` and `𝕄Vector₂` ($𝑷$).  See [Array of Matrices types](@ref).

Note that this function computes the following algebraic expression:

$\begin{pmatrix} B_1 & \hspace{0.01cm} & 0 \\ \hspace{0.01cm} & \ddots & \hspace{0.01cm} \\ 0 & \hspace{0.01cm} & B_m \end{pmatrix}  \begin{pmatrix} C_{11} & \cdots & C_{1m} \\ \vdots & \ddots & \vdots \\ C_{m1} & \cdots & C_{mm} \end{pmatrix}  \begin{pmatrix}B_1^T & \hspace{0.01cm} & 0 \\ \hspace{0.01cm} & \ddots & \hspace{0.01cm} \\ 0 & \hspace{0.01cm} & B_m^T\end{pmatrix}$ .

The result is a vector of vector of matrices of the `matrixVector₂Type`  argument, which must be provided and must be one of the following  abstract types: `ℍVector₂`, `𝔻Vector₂`, `𝕃Vector₂` or `𝕄Vector₂`  (and not an instance of these types).

When you pass it to this function, make sure to typecast $𝐁$  as an `ℍVector`, `𝔻Vector`, `𝕃Vector` or `𝕄Vector` type if it is not  already created as one of these types. See the example here below  and [typecasting matrices](@ref).

Method (2), (3) and (4) are **multi-threaded**. See [Threads](@ref).

!!! note "Nota Bene"
    Types `ℍ`, `𝔻`, `𝕃` or `𝕄` are actually constructors, thus they may modify the result of the congruence(s). This greatly expand the possibilities of this function, but it is your responsibility to pick the right argument `matrixType` in (1), `matrixVectorType` in (2) and `matrixVector₂Type` in (3)-(4). For example, in (1) if $B$ and $P$ are `Hermitian`, calling `cong(B, P, 𝔻)` will actually return the diagonal part of $B*P*B'$ and calling `cong(B, P, 𝕃)` will actually return its lower triangular part. The full congruence can be obtained as an `Hermitian` matrix by `cong(B, P, ℍ)` and as a generic matrix object by `cong(B, P, 𝕄)`.


**Examples**

```julia
using LinearAlgebra, PosDefManifold

# (1)
P=randP(3) # generate a 3x3 positive matrix
M=randn(3, 3)
C=cong(M, P, ℍ) # equivalent to C=ℍ(M*P*M')

# (2)
Pset=randP(4, 100); # generate 100 positive definite 4x4 matrices
M=randn(4, 4)
Qset=cong(M, Pset, ℍVector) # = [M*Pset_1*M',...,M*Pset_k*M'] as an ℍVector type

# recenter the matrices in Pset to their Fisher mean:
Qset=cong(invsqrt(mean(Fisher, Pset)), Pset, ℍVector)

# as a check, the Fisher mean of Qset is now the identity
mean(Fisher, Qset)≈I ? println("⭐") : println("⛔")

# (3)
Pset1=randP(4, 10); # generate 10 positive definite 4x4 matrices
Pset2=randP(4, 8);
Pset=ℍVector₂([Pset1, Pset2]);
M=randn(4, 4)
Qset=cong(M, Pset, MatrixVector₂)
Qset[1][1]≈M*Pset[1][1]*M' ? println("⭐") : println("⛔")
Qset[1][5]≈M*Pset[1][5]*M' ? println("⭐") : println("⛔")
Qset[2][1]≈M*Pset[2][1]*M' ? println("⭐") : println("⛔")
Qset[2][4]≈M*Pset[2][4]*M' ? println("⭐") : println("⛔")

# (4)
Pset1=randP(4, 2); # generate 2 positive definite 4x4 matrices
Pset2=randP(4, 2);
Pset=ℍVector₂([Pset1, Pset2]);
U=𝕄Vector([randU(4), randU(4)])
Qset=cong(U, Pset, MatrixVector₂)
Qset[1][1]≈U[1]*Pset[1][1]*U[1]' ? println("⭐") : println("⛔")
Qset[1][2]≈U[1]*Pset[1][2]*U[2]' ? println("⭐") : println("⛔")
Qset[2][1]≈U[2]*Pset[2][1]*U[1]' ? println("⭐") : println("⛔")
Qset[2][2]≈U[2]*Pset[2][2]*U[2]' ? println("⭐") : println("⛔")
```
