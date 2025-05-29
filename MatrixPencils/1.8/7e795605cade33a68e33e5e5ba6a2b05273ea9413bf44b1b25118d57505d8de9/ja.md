```
 pm2ls(P; contr = false, obs = false, noseig = false, minimal = false,
          fast = true, atol = 0, rtol) -> (A, E, B, C, D)
```

構造化された線形化をシステム行列 `S(λ)` として構築します。形式は次の通りです。

```
        | A-λE | B | 
 S(λ) = |------|---|
        |  C   | D |
```

多項式行列 `P(λ)` の一部のクロンカー構造を保持します。

`P(λ)` は、次の形式の次数 `k` の多項式行列として指定できます。`P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)` であり、係数行列 `P_i` は `i = 1, ..., k+1` の範囲で、3次元行列 `P` に格納されます。ここで `P[:,:,i]` は `i` 番目の係数行列 `P_i`（`λ**(i-1)` を掛けたもの）を含みます。

`P(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列、ベクトル、またはスカラーとしても指定できます。

`d` が `P(λ)` の次数で、`n` が `A-λE` の次数である場合、計算された線形化は次の条件を満たします。

(1) `A-λE` は正則であり、`P(λ) = C*inv(λE-A)*B+D` です；

(2) `rank[B A-λE] = n`（制御可能性）であり、`minimal = true` または `contr = true` の場合、右のクロンカー構造が保持されます；

(3) `rank[A-λE; C] = n`（可観測性）であり、`minimal = true` または `contr = true` の場合、左のクロンカー構造が保持されます；

(4) `A-λE` は非動的モードを持たない場合、`minimal = true` または `noseig = true` です。

条件 (1)-(4) が満たされる場合、線形化は `minimal` と呼ばれ、結果として得られる次数 `n` は達成可能な最小次数です。条件 (1)-(3) が満たされる場合、線形化は `irreducible` と呼ばれ、結果として得られる次数 `n` は直交類似変換を使用して達成可能な最小次数です。非可約線形化 `S(λ)` は、`P(λ)` の極-零構造（有限および無限）および左および右のクロンカー構造を保持します。

基礎となるペンシル操作アルゴリズム [1] および [2] は、次元削減線形化を計算するために、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解、または `fast = false` の場合はSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算コストは高くなります。

キーワード引数 `atol` および `rtol` は、それぞれ `P(λ)` の非ゼロ係数の絶対および相対許容誤差を指定します。

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[2] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017.  ```
