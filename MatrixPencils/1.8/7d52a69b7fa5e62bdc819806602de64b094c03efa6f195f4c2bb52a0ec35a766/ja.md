```
  rm2ls(NUM, DEN; contr = false, obs = false, noseig = false, minimal = false,
        fast = true, atol = 0, rtol) -> (A, E, B, C, D, blkdims)
```

構造化された線形化をシステム行列 `S(λ)` として次の形式で構築します。

```
           | A-λE | B | 
    S(λ) = |------|---|
           |  C   | D |
```

有理行列 `R(λ) = NUM(λ) ./ DEN(λ)` に対して、`S(λ)` が `R(λ)` のクロンカー構造の一部を保持するようにします。正則ペンシル `A-λE` はブロック対角形式を持ちます。

```
         | Af-λI |   0   | 
  A-λE = |-------|-------|
         |  0    | I-λEi |
```

および対角ブロック `Af` と `Ei` の次元は `blkdims[1]` と `blkdims[2]` に提供されます。

`NUM(λ)` は次の形式の多項式行列です。`NUM(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)` であり、係数行列 `N_i`（`i = 1, ..., k+1`）は3次元行列 `NUM` に格納されており、`NUM[:,:,i]` には `i` 番目の係数行列 `N_i`（`λ**(i-1)` を掛けたもの）が含まれています。

`DEN(λ)` は次の形式の多項式行列です。`DEN(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)` であり、係数行列 `D_i`（`i = 1, ..., l+1`）は3次元行列 `DEN` に格納されており、`DEN[:,:,i]` には `i` 番目の係数行列 `D_i`（`λ**(i-1)` を掛けたもの）が含まれています。

あるいは、`NUM(λ)` と `DEN(λ)` は [Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列として指定できます。この場合、`N(λ)` と `D(λ)` が同じ不確定要素を持つかどうかのチェックは行われません。

`n` が `A-λE` の次数である場合、計算された線形化は次の条件を満たします。

(1) `A-λE` は正則であり、`R(λ) = C*inv(λE-A)*B+D` です；

(2) `rank[B A-λE] = n` （制御可能性）であり、`minimal = true` または `contr = true` の場合、右のクロンカー構造が保持されます；

(3) `rank[A-λE; C] = n` （可観測性）であり、`minimal = true` または `obs = true` の場合、左のクロンカー構造が保持されます；

(4) `A-λE` は非動的モードを持たない場合、`minimal = true` または `noseig = true` です。

条件 (1)-(4) が満たされる場合、線形化は `minimal` と呼ばれ、結果として得られる次数 `n` は達成可能な最小次数です。条件 (1)-(3) が満たされる場合、線形化は `irreducible` と呼ばれ、結果として得られる次数 `n` は直交類似変換を使用して達成可能な最小次数です。非可約線形化 `S(λ)` は `R(λ)` の極-零構造（有限および無限）および左および右のクロンカー構造を保持します。

記述子システムに基づく線形化は、[1] に記載された方法とペンシル操作アルゴリズム [2] および [3] を組み合わせて使用して、縮小次数の線形化を計算します。これらのアルゴリズムは、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解を使用し、`fast = false` の場合はSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算努力は高くなります。

キーワード引数 `atol` と `rtol` は、それぞれ `NUM(λ)` と `DEN(λ)` の非ゼロ係数に対する絶対および相対許容誤差を指定します。

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[2] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[3] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017.  ```
