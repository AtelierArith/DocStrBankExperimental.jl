```
sys = dss(NUM, DEN; contr = false, obs = false, noseig = false, minimal = false, fast = true, atol = 0, rtol)
```

有理行列 `R(λ) = NUM(λ) ./ DEN(λ)` を、伝達関数行列が `R(λ)` であるような記述系表現 `sys = (A-λE,B,C,D)` に変換します。

`NUM(λ)` は、`NUM(λ) = N_1 + λ N_2 + ... + λ**k N_(k+1)` の形を持つ多項式行列であり、係数行列 `N_i`（`i = 1, ..., k+1`）は3次元行列 `NUM` に格納されており、`NUM[:,:,i]` には `N_i`（`λ**(i-1)` を掛けたもの）が含まれています。

`DEN(λ)` は、`DEN(λ) = D_1 + λ D_2 + ... + λ**l D_(l+1)` の形を持つ多項式行列であり、係数行列 `D_i`（`i = 1, ..., l+1`）は3次元行列 `DEN` に格納されており、`DEN[:,:,i]` には `D_i`（`λ**(i-1)` を掛けたもの）が含まれています。

あるいは、`NUM(λ)` と `DEN(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列として指定することもできます。

`n` が `A-λE` の次数である場合、計算された線形化は次の条件を満たします：

(1) `A-λE` は正則であり、`R(λ) = C*inv(λE-A)*B+D` です；

(2) `rank[B A-λE] = n` （制御可能性）もし `minimal = true` または `contr = true` の場合；

(3) `rank[A-λE; C] = n` （可観測性）もし `minimal = true` または `obs = true` の場合；

(4) `A-λE` に非動的モードが存在しない場合、もし `minimal = true` または `noseig = true` の場合。

条件 (1)-(4) が満たされる場合、実現は `minimal` と呼ばれ、得られる次数 `n` は達成可能な最小の次数です。条件 (1)-(3) が満たされる場合、実現は `irreducible` と呼ばれ、得られる次数 `n` は直交類似変換を使用した場合の達成可能な最小の次数です。非縮約実現は `R(λ)` の極-零点および特異構造を保持します。

記述系に基づく実現は、[1] に記載された方法と、縮小次数の実現を計算するためのペンシル操作アルゴリズム [2] および [3] を組み合わせて構築されます。これらのアルゴリズムは、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解を使用するか、`fast = false` の場合はSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算努力は高くなります。

キーワード引数 `atol` と `rtol` は、それぞれ `NUM(λ)` と `DEN(λ)` の非ゼロ係数に対する絶対および相対許容誤差を指定します。

[1] A. Varga, On computing the Kronecker structure of polynomial and rational matrices using Julia, 2020,  [arXiv:2006.06825](https://arxiv.org/pdf/2006.06825).

[2] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[3] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017.
