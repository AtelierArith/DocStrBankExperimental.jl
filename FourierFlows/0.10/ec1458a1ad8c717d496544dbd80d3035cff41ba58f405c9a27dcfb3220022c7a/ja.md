```
struct OneDGrid{T<:AbstractFloat, A, Tx, Tfft, Trfft, Talias} <: AbstractGrid{T, A, Talias, D}
```

1次元の `grid`。

  * `device::Any`: グリッドが存在するデバイス
  * `nx::Int64`: $x$ のポイント数
  * `nk::Int64`: $x$ の波数の数
  * `nkr::Int64`: $x$ の正の波数の数（実数フーリエ変換）
  * `dx::AbstractFloat`: $x$ のグリッド間隔
  * `Lx::AbstractFloat`: $x$ のドメインの範囲
  * `x::Any`: $x$-グリッドポイントの範囲
  * `k::Any`: $x$-波数の配列
  * `kr::Any`: 正の $x$-波数の配列（実数フーリエ変換）
  * `invksq::Any`: 逆二乗 $k$-波数の配列、$1 / k²$
  * `invkrsq::Any`: 逆二乗 $kᵣ$-波数の配列、$1 / kᵣ²$
  * `fftplan::Any`: 複素数値フィールドのためのFFTプラン
  * `rfftplan::Any`: 実数値フィールドのためのFFTプラン
  * `aliased_fraction::AbstractFloat`: エイリアスされた波数の割合（例：2次非線形性の場合は1/3）
  * `kalias::Any`: エイリアスされた $x$-波数のインデックスの範囲
  * `kralias::Any`: エイリアスされた正の $x$-波数のインデックスの範囲（実数フーリエ変換）
