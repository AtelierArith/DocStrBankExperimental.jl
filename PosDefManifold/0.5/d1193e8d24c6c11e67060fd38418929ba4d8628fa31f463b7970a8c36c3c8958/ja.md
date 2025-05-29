```
(1) congruence(B::AnyMatrix, P::AnyMatrix, matrixType)
(2) congruence(B::AnyMatrix, 𝐏::AnyMatrixVector, matrixVectorType)
(3) congruence(B::AnyMatrix, 𝑷::AnyMatrixVector₂, matrixVector₂Type)
(4) congruence(𝐁::AnyMatrixVector, 𝑷::AnyMatrixVector₂, matrixVector₂Type)

**エイリアス**: `cong`

(1) 同型変換を返します

$BPB^H$,

$B$ と $P$ は `Hermitian`、`LowerTriangular`、`Diagonal` または一般的な `Matrix` 型の任意の組み合わせです。

結果は `matrixType` 引数の型であり、提供されなければならず、これらの4つの抽象型のいずれかでなければなりません（それらのインスタンスではありません）。記号 `ℍ`、`𝔻`、`𝕃` および `𝕄` を使用してこれらの型を短縮する方法については、[aliases](@ref)を参照してください。

(2) 同型変換を保持する行列のベクトルを返します

$BP_kB^H$,

すべての $k$ 行列に対して $𝐏={P_1,...,P_k}$、$B$ と $𝐏$ は `Hermitian`、`LowerTriangular`、`Diagonal` または `Matrix` 型の任意の組み合わせです（$B$）および行列のベクトル型 `ℍVector`、`𝔻Vector`、`𝕃Vector` および `𝕄Vector` ($𝐏$)。行列の型については、[Array of Matrices types](@ref)を参照してください。

結果は `matrixVectorType` 引数の行列のベクトルであり、提供されなければならず、次の抽象型のいずれかでなければなりません: `ℍVector`、`𝔻Vector`、`𝕃Vector` または `𝕄Vector`（これらの型のインスタンスではありません）。

(3) 同型変換を保持する行列のベクトルのベクトルを返します

$BP_{mk}B^H$,

すべての $m$ ベクトルの $k[m]$ 行列のベクトルに対して $𝑷$、$B$ と $𝑷$ は `Hermitian`、`LowerTriangular`、`Diagonal` または `Matrix` 型の任意の組み合わせです（$B$）および行列のベクトル型 `ℍVector₂`、`𝔻Vector₂`、`𝕃Vector₂` および `𝕄Vector₂` ($𝑷$)。行列の型については、[Array of Matrices types](@ref)を参照してください。

結果は `matrixVector₂Type` 引数の行列のベクトルのベクトルであり、提供されなければならず、次の抽象型のいずれかでなければなりません: `ℍVector₂`、`𝔻Vector₂`、`𝕃Vector₂` または `𝕄Vector₂`（これらの型のインスタンスではありません）。

(4) 同型変換を保持する行列のベクトルのベクトルを返します

$B_iP_{ij}B_j^H$、$i,j∈[1,...,m]$。

$𝐁$ は $m$ 行列を保持し、$𝑷$ はそれぞれ $m$ 行列を保持する $m$ ベクトルを持ちます。注意すべきは、メソッド (3) とは異なり、ここでは $𝑷$ のベクトルはすべて同じ長さであり、これはちょうど $𝐁$ の長さです。$𝐁$ と $𝑷$ は行列のベクトル型 `ℍVector`、`𝔻Vector`、`𝕃Vector` および `𝕄Vector` ($𝐁$) と行列のベクトル型 `ℍVector₂`、`𝔻Vector₂`、`𝕃Vector₂` および `𝕄Vector₂` ($𝑷$) の任意の組み合わせである可能性があります。行列の型については、[Array of Matrices types](@ref)を参照してください。

この関数は次の代数式を計算します:

$\begin{pmatrix} B_1 & \hspace{0.01cm} & 0 \\ \hspace{0.01cm} & \ddots & \hspace{0.01cm} \\ 0 & \hspace{0.01cm} & B_m \end{pmatrix}  \begin{pmatrix} C_{11} & \cdots & C_{1m} \\ \vdots & \ddots & \vdots \\ C_{m1} & \cdots & C_{mm} \end{pmatrix}  \begin{pmatrix}B_1^T & \hspace{0.01cm} & 0 \\ \hspace{0.01cm} & \ddots & \hspace{0.01cm} \\ 0 & \hspace{0.01cm} & B_m^T\end{pmatrix}$ 。

結果は `matrixVector₂Type` 引数の行列のベクトルのベクトルであり、提供されなければならず、次の抽象型のいずれかでなければなりません: `ℍVector₂`、`𝔻Vector₂`、`𝕃Vector₂` または `𝕄Vector₂`（これらの型のインスタンスではありません）。

この関数に渡すときは、$𝐁$ を `ℍVector`、`𝔻Vector`、`𝕃Vector` または `𝕄Vector` 型として型キャストすることを確認してください。すでにこれらの型のいずれかとして作成されていない場合。以下の例を参照してください [typecasting matrices](@ref)。

メソッド (2)、(3) および (4) は **マルチスレッド** です。 [Threads](@ref)を参照してください。

!!! note "Nota Bene"
    型 `ℍ`、`𝔻`、`𝕃` または `𝕄` は実際にはコンストラクタであるため、同型変換の結果を変更する可能性があります。これにより、この関数の可能性が大幅に拡大しますが、(1) の引数 `matrixType`、(2) の `matrixVectorType`、(3)-(4) の `matrixVector₂Type` を正しく選択するのはあなたの責任です。たとえば、(1) で $B$ と $P$ が `Hermitian` の場合、`cong(B, P, 𝔻)` を呼び出すと、実際には $B*P*B'$ の対角部分が返され、`cong(B, P, 𝕃)` を呼び出すと、実際にはその下三角部分が返されます。完全な同型は `cong(B, P, ℍ)` によって `Hermitian` 行列として取得でき、一般的な行列オブジェクトとして `cong(B, P, 𝕄)` によって取得できます。

**例**

```

julia using LinearAlgebra, PosDefManifold

# (1)

P=randP(3) # 3x3 の正の行列を生成 M=randn(3, 3) C=cong(M, P, ℍ) # C=ℍ(M*P*M') と同等

# (2)

Pset=randP(4, 100); # 100 の正定値 4x4 行列を生成 M=randn(4, 4) Qset=cong(M, Pset, ℍVector) # = [M*Pset_1*M',...,M*Pset_k*M'] を ℍVector 型として

# Pset の行列をフィッシャー平均に再中心化:

Qset=cong(invsqrt(mean(Fisher, Pset)), Pset, ℍVector)

# チェックとして、Qset のフィッシャー平均は現在単位行列である

mean(Fisher, Qset)≈I ? println("⭐") : println("⛔")

# (3)

Pset1=randP(4, 10); # 10 の正定値 4x4 行列を生成 Pset2=randP(4, 8); Pset=ℍVector₂([Pset1, Pset2]); M=randn(4, 4) Qset=cong(M, Pset, MatrixVector₂) Qset[1][1]≈M*Pset[1][1]*M' ? println("⭐") : println("⛔") Qset[1][5]≈M*Pset[1][5]*M' ? println("⭐") : println("⛔") Qset[2][1]≈M*Pset[2][1]*M' ? println("⭐") : println("⛔") Qset[2][4]≈M*Pset[2][4]*M' ? println("⭐") : println("⛔")

# (4)

Pset1=randP(4, 2); # 2 の正定値 4x4 行列を生成 Pset2=randP(4, 2); Pset=ℍVector₂([Pset1, Pset2]); U=𝕄Vector([randU(4), randU(4)]) Qset=cong(U, Pset, MatrixVector₂) Qset[1][1]≈U[1]*Pset[1][1]*U[1]' ? println("⭐") : println("⛔") Qset[1][2]≈U[1]*Pset[1][2]*U[2]' ? println("⭐") : println("⛔") Qset[2][1]≈U[2]*Pset[2][1]*U[1]' ? println("⭐") : println("⛔") Qset[2][2]≈U[2]*Pset[2][2]*U[2]' ? println("⭐") : println("⛔") ```
