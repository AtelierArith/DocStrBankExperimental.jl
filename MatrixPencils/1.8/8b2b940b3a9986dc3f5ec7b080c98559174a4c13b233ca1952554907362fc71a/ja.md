```
rmpoles(N, D; fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, ip, id)
```

有理行列 `R(λ) := N(λ)./D(λ)` の有限および無限の極を `val` に、無限の極の重複度を `ip` に、基礎となる不可約記述系に基づく線形化の極ペンシルの無限の基本除数を `id` に返します。

有理行列 `R(λ)` の有限および無限の極に関する情報は、[1] および [2] の結果を使用して、基礎となる線形化のクロンカー構造情報から取得されます。クロンカー構造情報の決定は、`R(λ) = C*inv(λE-A)*B+D` を満たすように、`A-λE` が次数 `n` の正則ペンシルである不可約記述系の実現 `(A-λE,B,C,D)` を構築することによって行われ、正則ペンシル `A-λE` を有限の固有値（`R(λ)` の有限極でもある）と無限の固有値の重複度（`R(λ)` の無限極の重複度に対して1つ余分）を示す適切なクロンカー様形式（KLF）に還元します。`A-λE` の無限のゼロの重複度と `R(λ)` の無限の極の重複度は同じであり、`ip` に返されます。`val` の無限の極の数は `ip` の重複度の合計に等しいです。`A-λE` の無限の固有値の重複度は `id` に返されます。

分子 `N(λ)` は、`N(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)` の形の多項式行列であり、係数行列 `N_i`（`i = 1, ..., k+1`）は3次元行列 `N` に格納され、`N[:,:,i]` には `λ**(i-1)` を掛けた `i` 番目の係数行列 `N_i` が含まれます。

分母 `D(λ)` は、`D(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)` の形の多項式行列であり、係数行列 `D_i`（`i = 1, ..., l+1`）は3次元行列 `D` に格納され、`D[:,:,i]` には `λ**(i-1)` を掛けた `i` 番目の係数行列 `D_i` が含まれます。

あるいは、`N(λ)` と `D(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列として指定できます。この場合、`N(λ)` と `D(λ)` が同じ不確定要素を持つかどうかのチェックは行われません。

不可約記述系に基づく線形化は、[3] に記載された方法を使用し、[4] および [5] のペンシル操作アルゴリズムと組み合わせて、縮小次数の線形化を計算します。これらのアルゴリズムは、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解を使用し、`fast = false` の場合はSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性が高いですが、関与する計算コストは高くなります。

`A-λE` のKLFへの還元は、直交類似変換を使用して行われ、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づくランク決定を含み、`fast = false` の場合はより信頼性の高いSVD分解を含みます。効率のために、還元は部分的にのみ行われ、実行された直交変換は蓄積されません。

キーワード引数 `atol` と `rtol` は、それぞれ `N(λ)` と `D(λ)` の非ゼロ係数の絶対および相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は `N(λ)` の最小次元のサイズで、`ϵ` は `N(λ)` の係数の要素型の機械イプシロンです。

[1] G. Verghese, B. Levy, and T. Kailath, Generalized state-space systems, IEEE Trans. Automat. Control, 26:811-831 (1981).

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.

[3] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[4] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[5] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
