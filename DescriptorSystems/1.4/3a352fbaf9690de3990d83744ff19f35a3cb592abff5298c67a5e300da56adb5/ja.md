```
sys = dss(P; Ts = 0, contr = false, obs = false, noseig = false, minimal = false, fast = true, atol = 0, rtol)
```

多項式行列 `P(λ)` を記述子システム表現 `sys = (A-λE,B,C,D)` に変換します。このとき、`sys` の伝達関数行列は `P(λ)` になります。`Ts = 0` の場合、得られる `sys` は連続時間システムであり、`Ts = -1` または `Ts > 0` の場合は離散時間システムになります。

`P(λ)` は、`P(λ) = P_1 + λ P_2 + ... + λ**k P_(k+1)` の形の次数 `k` の多項式行列として指定できます。このとき、係数行列 `P_i`（`i = 1, ..., k+1`）は3次元行列 `P` に格納され、`P[:,:,i]` には `λ**(i-1)` を掛けた `i` 番目の係数行列 `P_i` が含まれます。

`P(λ)` は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型の要素の行列、ベクトル、またはスカラーとしても指定できます。

`d` を `P(λ)` の次数、`n` を `A-λE` の次数とすると、計算された実現は次の条件を満たします：

(1) `A-λE` は正則であり、`P(λ) = C*inv(λE-A)*B+D` です；

(2) `rank[B A-λE] = n` （制御可能性）であり、`minimal = true` または `contr = true` の場合；

(3) `rank[A-λE; C] = n` （可観測性）であり、`minimal = true` または `contr = true` の場合；

(4) `A-λE` に非動的モードが存在しない場合、`minimal = true` または `noseig = true` です。

条件 (1)-(4) が満たされる場合、実現は `minimal` と呼ばれ、得られる次数 `n` は達成可能な最小の次数です。条件 (1)-(3) が満たされる場合、実現は `irreducible` と呼ばれ、得られる次数 `n` は直交類似変換を使用した場合の達成可能な最小の次数です。非縮約実現は `P(λ)` の極-零点および特異構造を保持します。

基礎となるペンシル操作アルゴリズム [1] と [2] は、縮小次数の実現を計算するために、`fast = true` の場合は列ピボッティングを伴うランク明示QR分解、`fast = false` の場合はSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性が高いですが、関与する計算コストは高くなります。

キーワード引数 `atol` と `rtol` は、それぞれ `P(λ)` の非ゼロ係数に対する絶対および相対許容誤差を指定します。

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[2] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017. 
