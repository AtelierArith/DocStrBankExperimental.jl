```
(1) quadraticForm(v::Vector{T}, P::ℍ{T}) where T<:Real
(2) quadraticForm(v::Vector{T}, L::𝕃{T}) where T<:Real
(3) quadraticForm(v::Vector{T}, X::𝕄{T}, forceLower::Bool=false) where T<:Real
(4) quadraticForm(v::Vector{S}, X::Union{𝕄{S}, ℍ{S}, 𝕃{S}}) where S<:Complex

**エイリアス**: `qf`

(1) 実ベクトル $v$ と実 `Hermitian` 行列 $P$ が与えられたとき、二次形式を計算します

$v^TPv$,

ここで、上付き文字 *T* は転置を示します。 $P$ の下三角部分のみを使用します。

(2) (1) と同様に、実ベクトル $v$ と `LowerTriangular` 行列 $L$ が与えられたとき。

(3) (1) と同様に、実ベクトル $v$ と実一般行列 $M$ が与えられたとき、`forceLower=true` の場合。 `forceLower=false` の場合、積 $v^TMv$ が代わりに全行列 $M$ を使用して評価されます。

(4) 複素ベクトル `v` と複素 `Matrix`、`LowerTriangular` または `Hermitian` 行列に対して、二次形式 $v^HPv$ を計算します。全行列が使用されます。

## 数学

$v$ と $X$ が実で $X$ が対称である場合、二次形式は

$\sum_i(v_i^2x_{ii})+\sum_{i>j}(2v_iv_jx_{ij})$。

$L$ が下三角の場合は

$\sum_i(v_i^2x_{ii})+\sum_{i>j}(v_iv_jx_{ij})$。

これらの式はメソッド (1)、(2) および (3) で使用されます。

**例**

```

julia using PosDefManifold P=randP(5) # 5x5 のランダムな実正定値行列を生成 v=randn(5) q1=quadraticForm(v, P) # または q1=qf(v, P) q2=v'*P*v q1 ≈ q2 ? println(" ⭐ ") : println(" ⛔ ") ```
