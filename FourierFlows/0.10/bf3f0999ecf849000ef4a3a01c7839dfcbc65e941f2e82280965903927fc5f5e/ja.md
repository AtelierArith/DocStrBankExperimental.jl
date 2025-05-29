```
struct TwoDGrid{T<:AbstractFloat, A, Tx, Tfft, Trfft, Talias, D} <: AbstractGrid{T, Tk, Talias, D}
```

二次元の `grid`。

  * `device::Any`: グリッドが存在するデバイス
  * `nx::Int64`: $x$ のポイント数
  * `ny::Int64`: $y$ のポイント数
  * `nk::Int64`: $x$ の波数の数
  * `nl::Int64`: $y$ の波数の数
  * `nkr::Int64`: $x$ の正の波数の数（実数フーリエ変換）
  * `dx::AbstractFloat`: $x$ のグリッド間隔
  * `dy::AbstractFloat`: $y$ のグリッド間隔
  * `Lx::AbstractFloat`: $x$ のドメインの範囲
  * `Ly::AbstractFloat`: $y$ のドメインの範囲
  * `x::Any`: $x$-グリッドポイントの範囲
  * `y::Any`: $y$-グリッドポイントの範囲
  * `k::Any`: $x$-波数の配列
  * `l::Any`: $y$-波数の配列
  * `kr::Any`: 正の $x$-波数の配列（実数フーリエ変換）
  * `Ksq::Any`: 二乗された総波数の配列、$k² + l²$
  * `invKsq::Any`: 逆二乗された総波数の配列、$1 / (k² + l²)$
  * `Krsq::Any`: 実数フーリエ変換のための二乗された総波数の配列、$kᵣ² + l²$
  * `invKrsq::Any`: 実数フーリエ変換のための逆二乗された総波数の配列、$1 / (kᵣ² + l²)$
  * `fftplan::Any`: 複素値フィールドのためのFFTプラン
  * `rfftplan::Any`: 実値フィールドのためのFFTプラン
  * `aliased_fraction::AbstractFloat`: エイリアスされた波数の割合（例：二次非線形性の場合は1/3）
  * `kalias::Any`: エイリアスされた $x$-波数のインデックスの範囲
  * `kralias::Any`: エイリアスされた正の $x$-波数のインデックスの範囲（実数フーリエ変換）
  * `lalias::Any`: エイリアスされた $y$-波数のインデックスの範囲
