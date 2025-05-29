```
rmpoles1(N, D;  fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, ip, id)
```

有理行列 `R(λ) := N(λ)./D(λ)` の有限および無限の極を `val` に、無限の極の重複度を `ip` に、基礎となる強い不可約ペンシルに基づく線形化の極ペンシルの無限の基本除数を `id` に返します。

有理行列 `R(λ)` の有限および無限の極に関する情報は、基礎となるペンシルに基づく線形化の極構造情報から得られます。極構造情報の決定は、`R(λ) = (C-λG)*inv(λE-A)*(B-λF)+D-λH` を満たす正則ペンシル `A-λE` の順序 `n` の強い最小ペンシルに基づく線形化 `(A-λE,B-λF,C-λG,D-λH)` を構築することによって行われ、有限の固有値の数（また `R(λ)` の有限極でもある）と無限の固有値の重複度を示す適切なクロンカー様式（KLF）に構造化されたシステム行列ペンシル `Sp(λ) = [A-λE -λF; -λG -λH]` を削減します。`Sp(λ)` の無限のゼロの重複度と `R(λ)` の無限の極の重複度は同じであり、`ip` に返されます。`val` の無限の極の数は `ip` の重複度の合計に等しいです。`Sp(λ)` の無限の固有値の重複度は `id` に返されます。

分子 `N(λ)` は、`N(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)` の形の多項式行列であり、係数行列 `N_i`（`i = 1, ..., k+1`）は3次元行列 `N` に格納され、`N[:,:,i]` には `i` 番目の係数行列 `N_i`（`λ**(i-1)` を掛けたもの）が含まれます。

分母 `D(λ)` は、`D(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)` の形の多項式行列であり、係数行列 `D_i`（`i = 1, ..., l+1`）は3次元行列 `D` に格納され、`D[:,:,i]` には `i` 番目の係数行列 `D_i`（`λ**(i-1)` を掛けたもの）が含まれます。

また、`N(λ)` と `D(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列として指定することもできます。この場合、`N(λ)` と `D(λ)` が同じ不確定要素を持つかどうかのチェックは行われません。

強い最小ペンシルに基づく線形化は、[3] に記載された方法と、削減された順序の線形化を計算するための [4] のペンシル操作アルゴリズムを組み合わせて構築されます。これらのアルゴリズムは、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解を使用するか、`fast = false` の場合はSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性が高いですが、関与する計算コストは高くなります。

`Sp(λ)` のKLFへの削減は、直交類似変換 [5] を使用して行われ、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づくランク決定、または `fast = false` の場合はより信頼性の高いSVD分解に基づくランク決定が含まれます。効率のために、削減は部分的にのみ行われ、実行された直交変換を累積することはありません。

キーワード引数 `atol` と `rtol` は、それぞれ `N(λ)` と `D(λ)` の非ゼロ係数に対する絶対および相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は `N(λ)` の最小次元のサイズで、`ϵ` は `N(λ)` の係数の要素型のマシンエプシロンです。

[1] G. Verghese, B. Levy, and T. Kailath, Generalized state-space systems, IEEE Trans. Automat. Control, 26:811-831 (1981).

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.

[3] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[4] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions, to appear in "Realization and Model Reduction of Dynamical Systems",  A Festschrift to honor the 70th birthday of Thanos Antoulas", Springer-Verlag. [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf)

[5] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
