```
pmpoles1(P; fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, ip, id)
```

多項式行列 `P(λ)` の無限極を `val` に、無限極の重複度を `ip` に、基になる強い不可約ペンシルに基づく極ペンシル `Sp(λ)` の無限基本除数を `id` に返します。

`P(λ)` は、`P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)` の形の次数 `k` の多項式行列として指定でき、係数行列 `P_i`（`i = 1, ..., k+1`）は3次元行列 `P` に格納され、`P[:,:,i]` には `i` 番目の係数行列 `P_i`（`λ**(i-1)` を掛けたもの）が含まれます。

`P(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列、ベクトル、またはスカラーとしても指定できます。

多項式行列 `P(λ)` の無限極に関する情報は、[1] および [2] の結果を使用して、基になるペンシルに基づく線形化の極構造情報から取得されます。極構造情報の決定は、`A-λE` が正則ペンシルであり、`P(λ) = (C-λG)*inv(λE-A)*(B-λF)+D-λH` を満たす強い最小ペンシルに基づく線形化 `(A-λE,B-λF,C-λG,D-λH)` を構築することによって行われ、無限固有値の重複度を示す適切なクロンカー様形式 (KLF) に極系行列ペンシル `Sp(λ) = [A-λE -λF; -λG -λH]` を縮約します。`Sp(λ)` の無限ゼロの重複度と `P(λ)` の無限極の重複度は同じであり、`ip` に返されます。`val` の無限極の数は `ip` の重複度の合計に等しく、`Sp(λ)` の無限固有値の重複度は `id` に返されます。

`Sp(λ)` を KLF に縮約するためには、直交類似変換を使用し、列ピボットを伴うランクを明らかにするQR分解に基づくランク決定を含みます。`fast = true` の場合は、より信頼性の高いSVD分解を使用します。効率のために、縮約は部分的にのみ行われ、実行された直交変換は蓄積されません。

キーワード引数 `atol` と `rtol` は、それぞれ `P(λ)` の非ゼロ係数の絶対および相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は `P(λ)` の最小次元のサイズで、`ϵ` は `P(λ)` の係数の要素型のマシンイプシロンです。

[1] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions, to appear in "Realization and Model Reduction of Dynamical Systems",  A Festschrift to honor the 70th birthday of Thanos Antoulas", Springer-Verlag. [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf)

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.
