```
   rmrank(N, D; fastrank = true, atol = 0, rtol = atol > 0 ? 0 : n*ϵ)
```

有理行列 `R(λ) := N(λ)./D(λ)` の通常のランクを決定します。

`fastrank = true` の場合、ランクは `R(γ)` の特異値のうち、絶対値が `max(atol, rtol*σ₁)` より大きいものの数を数えることによって評価されます。ここで `σ₁` は `R(γ)` の最大特異値であり、`γ` は絶対値が1のランダムに生成された複素数です。`fastrank = false` の場合、まず `R(λ)` の構造化線形化が、`S(λ) = [A-λE B; C D]` の形の記述子システム行列として構築され、`A-λE` は次数 `n` の正則サブペンシルであり、その後、通常のランク `nr` が決定されます。`R(λ)` の通常のランクは `nr - n` です。

分子 `N(λ)` は、`N(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)` の形の多項式行列であり、係数行列 `N_i`（`i = 1, ..., k+1`）は3次元行列 `N` に格納され、`N[:,:,i]` には `i` 番目の係数行列 `N_i`（`λ**(i-1)` を掛けたもの）が含まれます。

分母 `D(λ)` は、`D(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)` の形の多項式行列であり、係数行列 `D_i`（`i = 1, ..., l+1`）は3次元行列 `D` に格納され、`D[:,:,i]` には `i` 番目の係数行列 `D_i`（`λ**(i-1)` を掛けたもの）が含まれます。

また、`N(λ)` と `D(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列として指定することもできます。この場合、`N(λ)` と `D(λ)` が同じ不確定要素を持つかどうかのチェックは行われません。

不可約な記述子システムに基づく線形化は、[1] に記載された方法と、[2] および [3] のペンシル操作アルゴリズムを組み合わせて、縮小次数の線形化を計算するために構築されます。これらのアルゴリズムは、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解を使用し、`fast = false` の場合はSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算コストは高くなります。

`S(λ)` の適切なKLFへの削減は、直交相似変換 [3] を使用して行われ、ランクを明らかにするSVD分解に基づくランク決定が含まれます。

キーワード引数 `atol` と `rtol` は、それぞれ `N(λ)` と `D(λ)` の非ゼロ係数の絶対および相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は `N(λ)` の最小次元のサイズで、`ϵ` は `N(λ)` の係数の要素型のマシンイプシロンです。

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[2] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[3] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
