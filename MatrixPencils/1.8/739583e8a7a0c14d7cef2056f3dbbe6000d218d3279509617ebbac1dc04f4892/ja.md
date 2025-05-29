```
 rm2lps(NUM, DEN; contr = false, obs = false) -> (A, E, B, F, C, G, D, H, blkdims)
```

構造化されたペンシルに基づく線形化を、次の形式のシステム行列 `S(λ)` として構築します。

```
        | A-λE | B-λF | 
 S(λ) = |------|------|
        | C-λG | D-λH |
```

有理行列 `R(λ) = NUM(λ) ./ DEN(λ)` に対して、`S(λ)` が `R(λ)` のクロンカー構造の一部を保持するようにします。通常のペンシル `A-λE` はブロック対角形式を持ちます。

```
         | Af-λI |   0    | 
  A-λE = |-------|--------|
         |  0    | Ai-λEi |
```

および対角ブロック `Af` と `Ai` の次元は `blkdims[1]` と `blkdims[2]` に提供されます。

`NUM(λ)` は次の形式の多項式行列です。`NUM(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)` であり、係数行列 `N_i`（`i = 1, ..., k+1`）は3次元行列 `NUM` に格納されており、`NUM[:,:,i]` には `i` 番目の係数行列 `N_i`（`λ**(i-1)` を掛けたもの）が含まれています。

`DEN(λ)` は次の形式の多項式行列です。`DEN(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)` であり、係数行列 `D_i`（`i = 1, ..., l+1`）は3次元行列 `DEN` に格納されており、`DEN[:,:,i]` には `i` 番目の係数行列 `D_i`（`λ**(i-1)` を掛けたもの）が含まれています。

あるいは、`NUM(λ)` と `DEN(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列として指定することもできます。この場合、`N(λ)` と `D(λ)` が同じ不確定要素を持つかどうかのチェックは行われません。

`n` が行列 `A` の次数である場合、計算された線形化は次の条件を満たします。

(1) `A-λE` は `n x n` の通常のペンシルです；

(2) `R(λ) = (C-λG)*inv(λE-A)*(B-λF)+D-λH`；

(3) `rank[B-λF A-λE] = n` は任意の有限および無限の `λ` に対して成り立ちます（強い制御可能性）。この場合、右のクロンカー構造が保持されます；

(4) `rank[A-λE; C-λG] = n` は任意の有限および無限の `λ` に対して成り立ちます（強い可観測性）。この場合、左のクロンカー構造が保持されます。

条件 (1)-(4) が満たされる場合、線形化は「強い最小」と呼ばれ、得られる次数 `n` は達成可能な最小次数であり、`S(λ)` は `R(λ)` の極-零構造（有限および無限）および左と右のクロンカー構造を保持します。

ペンシルに基づく線形化は、[1] に記載された方法と、次元削減線形化を計算するためのペンシル操作アルゴリズム [2] および [3] を組み合わせて構築されます。これらのアルゴリズムは、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解を使用し、`fast = false` の場合はSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算努力は高くなります。

キーワード引数 `atol` と `rtol` は、それぞれ `NUM(λ)` と `DEN(λ)` の非ゼロ係数に対する絶対および相対許容誤差を指定します。

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[2] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[3] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions,  in "Realization and Model Reduction of Dynamical Systems, A Festschrift to honor the 70th birthday of Thanos Antoulas",  Eds. C. Beattie, P. Benner, M. Embree, S. Gugercin and S. Lefteriu, Springer-Verlag, 2020.  [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf)
