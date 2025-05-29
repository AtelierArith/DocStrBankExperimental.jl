```
rmzeros(N, D; fast = false, atol::Real = 0, rtol::Real = atol>0 ? 0 : n*ϵ) -> (val, iz, KRInfo)
```

有理行列 `R(λ) := N(λ)./D(λ)` の有限および無限のゼロを `val` に、無限のゼロの重複度を `iz` に、そして有理行列 `R(λ)` のクロンネッカー構造に関する情報を `KRInfo` オブジェクトに返します。

有理行列 `R(λ)` のクロンネッカー構造に関する情報は、右クロンネッカー指標 `rki`、左クロンネッカー指標 `lki`、有限ゼロの数 `nf`、および通常のランク `nrank` で構成され、これらはそれぞれ `KRInfo.rki`、`KRInfo.lki`、`KRInfo.nf`、`KRInfo.nrank` から取得できます。詳細については、[`KRInfo`](@ref) を参照してください。さらに、`KRInfo.id` には、基礎となる線形化の無限の基本因子が構造化されたシステム行列ペンシルとして含まれています。

有理行列 `R(λ)` のクロンネッカー構造情報は、基礎となる線形化のクロンネッカー構造情報から [1] および [2] の結果を使用して取得されます。クロンネッカー構造情報の決定は、`A-λE` が次数 `n` の正則ペンシルである不可約記述子システム実現 `(A-λE,B,C,D)` を構築することによって行われ、`R(λ) = C*inv(λE-A)*B+D` を満たし、構造化されたシステム行列ペンシル `S(λ) = [A-λE B; C D]` を有限固有値の数（`R(λ)` の有限ゼロでもある）、無限固有値の重複度（`R(λ)` の無限ゼロの重複度に1を加えたもの）、左および右のクロンネッカー指標（`R(λ)` のものでもある）、および通常のランク（`R(λ)` の通常のランクに `n` を加えたもの）を示す適切なクロンネッカー様形式（KLF）に還元します。

分子 `N(λ)` は、`N(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)` の形の多項式行列であり、係数行列 `N_i`（`i = 1, ..., k+1`）は3次元行列 `N` に格納され、`N[:,:,i]` には `i` 番目の係数行列 `N_i`（`λ**(i-1)` を掛けたもの）が含まれています。

分母 `D(λ)` は、`D(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)` の形の多項式行列であり、係数行列 `D_i`（`i = 1, ..., l+1`）は3次元行列 `D` に格納され、`D[:,:,i]` には `i` 番目の係数行列 `D_i`（`λ**(i-1)` を掛けたもの）が含まれています。

あるいは、`N(λ)` と `D(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列として指定することもできます。この場合、`N(λ)` と `D(λ)` が同じ不確定要素を持つかどうかのチェックは行われません。

不可約記述子システムに基づく線形化は、[3] に記載された方法を使用し、[4] および [5] のペンシル操作アルゴリズムと組み合わせて、縮小次数の線形化を計算します。これらのアルゴリズムは、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解を使用し、`fast = false` の場合はSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算コストは高くなります。

`S(λ)` の適切なKLFへの還元は、直交類似変換 [5] を使用して行われ、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づくランク決定、または `fast = false` の場合はより信頼性の高いSVD分解に基づくランク決定が含まれます。

キーワード引数 `atol` と `rtol` は、それぞれ `N(λ)` と `D(λ)` の非ゼロ係数に対する絶対および相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は `N(λ)` の最小次元のサイズで、`ϵ` は `N(λ)` の係数の要素型のマシンエプシロンです。

[1] G. Verghese, B. Levy, and T. Kailath, Generalized state-space systems, IEEE Trans. Automat. Control, 26:811-831 (1981).

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.

[3] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[4] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[5] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017.  ```
