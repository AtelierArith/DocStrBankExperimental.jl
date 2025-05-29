```
pmzeros1(P; fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, iz, KRInfo)
```

多項式行列 `P(λ)` の有限および無限のゼロを `val` に、無限のゼロの重複度を `iz` に、`P(λ)` の基になる強い不可約ペンシルに基づく線形化のクロンカー構造に関する情報を `KRInfo` オブジェクトに返します。

基になる線形化のクロンカー構造に関する情報は、右クロンカー指標 `rki`（`P(λ)` と同じ）、左クロンカー指標 `lki`（`P(λ)` と同じ）、無限の基本因子 `id`、有限の固有値の数 `nf`（`P(λ)` と同じ）、および通常のランク 'nrank' で構成され、`KRInfo` から `KRInfo.rki`、`KRInfo.lki`、`KRInfo.id`、`KRInfo.nf`、および `KRInfo.nrank` として取得できます。詳細については、[`KRInfo`](@ref) を参照してください。

`P(λ)` は、`P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)` の形の次数 `k` の多項式行列として指定でき、係数行列 `P_i`（`i = 1, ..., k+1`）は3次元行列 `P` に格納され、`P[:,:,i]` には `i` 番目の係数行列 `P_i`（`λ**(i-1)` を掛けたもの）が含まれます。

`P(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列、ベクトル、またはスカラーとしても指定できます。

ゼロの計算は、まず `P(λ)` の強い不可約ペンシルに基づく線形化を構築することによって行われます [1]。これは構造化されたシステム行列ペンシルとして次のように表されます。

```
          | A-λE | B-λF | 
 M - λN = |------|------| ,
          | C-λG | D-λH |
```

このとき、`P(λ) = (C-λG)*inv(λE-A)*(B-λF)+D-λH` となり、次にペンシル `M-λN` をそのクロンカー構造に関する情報を示す適切なクロンカー様式（KLF）に削減します。`M-λN` と `P(λ)` の左および右のクロンカー指標は同じ [2] であり、`KRInfo.rki` および `KRInfo.rki` にそれぞれ返されます。`M-λN` と `P(λ)` の無限のゼロの重複度は同じ [2] であり、`iz` に返されます。`val` の有限ゼロの数は `M-λN` の有限固有値の数（`KRInfo.nf` に返される）と等しく、`val` の無限ゼロの数は `iz` の重複度の合計です。`P(λ)` の通常のランクは `KRInfo.nrank - ν` として評価できます。

`M-λN` を KLF に削減するには、直交類似変換を使用し、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づくランク決定を含み、`fast = false` の場合はより信頼性の高いSVD分解を使用します。効率のために、削減は部分的にのみ行われ、実行された直交変換は蓄積されません。

キーワード引数 `atol` および `rtol` は、`P(λ)` の非ゼロ係数の絶対および相対許容誤差をそれぞれ指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は `P(λ)` の最小次元のサイズで、`ϵ` は `P(λ)` の係数の要素型のマシンエプシロンです。

[1] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions, to appear in "Realization and Model Reduction of Dynamical Systems", A Festschrift to honor the 70th birthday of Thanos Antoulas", Springer-Verlag. [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf)

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009. ```
