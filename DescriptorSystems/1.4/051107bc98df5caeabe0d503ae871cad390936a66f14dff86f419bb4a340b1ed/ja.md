```
sys = dss(R; Ts=missing, contr = false, obs = false, noseig = false, minimal = false, fast = true, atol = 0, rtol)
```

有理伝達関数行列 `R(λ)` を、伝達関数行列 `R(λ)` に対して `sys = (A-λE,B,C,D)` という形の記述系表現に変換します。`Ts = 0` の場合は連続時間システム、`Ts = -1` または `Ts > 0` の場合は離散時間システムになります。`Ts = missing` の場合、`sys` のサンプリング時間は `R` の要素のサンプリング時間 `TRs` から引き継がれます。ただし、`TRs = nothing` の場合はデフォルトで `Ts = 0` が使用されます。

`R(λ)` は、有理伝達関数のエントリを持つ行列です（[`RationalTransferFunction`](@ref) を参照）で、複数入力複数出力システムまたは単一入力単一出力システムに対応する有理伝達関数です。`R` の要素の分子と分母は、[Polynomials](https://github.com/JuliaMath/Polynomials.jl) パッケージによって提供される `Polynomial` 型です。

`n` が `A-λE` の次数である場合、計算された実現は次の条件を満たします：

(1) `A-λE` は正則であり、`R(λ) = C*inv(λE-A)*B+D` です；

(2) `rank[B A-λE] = n` （制御可能性）で、`minimal = true` または `contr = true` の場合；

(3) `rank[A-λE; C] = n` （可観測性）で、`minimal = true` または `contr = true` の場合；

(4) `A-λE` に非動的モードが存在しない場合、`minimal = true` または `noseig = true` の場合。

条件 (1)-(4) が満たされる場合、その実現は `minimal` と呼ばれ、結果として得られる次数 `n` は達成可能な最小の次数です。条件 (1)-(3) が満たされる場合、その実現は `irreducible` と呼ばれ、結果として得られる次数 `n` は直交類似変換を使用して達成可能な最小の次数です。非還元実現は、`R(λ)` の極-零点および特異構造を保持します。

基礎となるペンシル操作アルゴリズム [1] と [2] は、縮小次数の実現を計算するために、`fast = true` の場合は列ピボットを用いたランク明示QR分解、`fast = false` の場合はSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算努力は高くなります。

キーワード引数 `atol` と `rtol` は、`R(λ)` の非ゼロ係数に対する絶対および相対許容誤差を指定します。

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[2] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017.  ```
