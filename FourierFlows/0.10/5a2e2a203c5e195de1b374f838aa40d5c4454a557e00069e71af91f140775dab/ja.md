```
struct ThreeDGrid{T<:AbstractFloat, Tk, Tx, Tfft, Trfft, Talias} <: AbstractGrid{T, Tk, Talias}
```

三次元の `grid`。

  * `device::Any`: グリッドが存在するデバイス
  * `nx::Int64`: $x$ のポイント数
  * `ny::Int64`: $y$ のポイント数
  * `nz::Int64`: $z$ のポイント数
  * `nk::Int64`: $x$ の波数の数
  * `nl::Int64`: $y$ の波数の数
  * `nm::Int64`: $z$ の波数の数
  * `nkr::Int64`: $x$ の正の波数の数（実フーリエ変換）
  * `dx::AbstractFloat`: $x$ のグリッド間隔
  * `dy::AbstractFloat`: $y$ のグリッド間隔
  * `dz::AbstractFloat`: $z$ のグリッド間隔
  * `Lx::AbstractFloat`: $x$ のドメインの範囲
  * `Ly::AbstractFloat`: $y$ のドメインの範囲
  * `Lz::AbstractFloat`: $z$ のドメインの範囲
  * `x::Any`: $x$-グリッドポイントの範囲
  * `y::Any`: $y$-グリッドポイントの範囲
  * `z::Any`: $z$-グリッドポイントの範囲
  * `k::Any`: $x$-波数の配列
  * `l::Any`: $y$-波数の配列
  * `m::Any`: $z$-波数の配列
  * `kr::Any`: 正の $x$-波数の配列（実フーリエ変換）
  * `Ksq::Any`: 二乗された総波数の配列、$k² + l² + m²$
  * `invKsq::Any`: 逆二乗された総波数の配列、$1 / (k² + l² + m²)$
  * `Krsq::Any`: 実フーリエ変換のための二乗された総波数の配列、$kᵣ² + l² + m²$
  * `invKrsq::Any`: 実フーリエ変換のための逆二乗された総波数の配列、$1 / (kᵣ² + l² + m²)$
  * `fftplan::Any`: 複素値フィールドのためのFFTプラン
  * `rfftplan::Any`: 実値フィールドのためのFFTプラン
  * `aliased_fraction::AbstractFloat`: エイリアスされた波数の割合（例：二次非線形性のための1/3）
  * `kalias::Any`: エイリアスされた $x$-波数のインデックスの範囲
  * `kralias::Any`: エイリアスされた正の $x$-波数のインデックスの範囲（実フーリエ変換）
  * `lalias::Any`: エイリアスされた $y$-波数のインデックスの範囲
  * `malias::Any`: エイリアスされた $m$-波数のインデックスの範囲
