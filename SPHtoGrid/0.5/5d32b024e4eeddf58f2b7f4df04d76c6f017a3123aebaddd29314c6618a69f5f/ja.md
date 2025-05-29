```
healpix_map(Pos, Hsml, M, Rho, Bin_q, Weights;
            center::Vector{<:Real}=[0.0, 0.0, 0.0],
            radius_limits::Vector{<:Real}=[0.0, Inf],
            Nside::Integer=1024,
            kernel::AbstractSPHKernel,
            calc_mean::Bool=true
            show_progress::Bool=true,
            output_from_all_workers::Bool=false)
```

SPH粒子から全空のマップを計算します。二つの`HealpixMap`を返します: `(image, weight_image)`。画像を減少させるには、`image`を`weight_image`で割ります。

## 引数:

  * `Pos`: 物理コード単位での粒子の位置
  * `HSML`: 物理コード単位での粒子のhsml
  * `M`: 物理コード単位での粒子の質量
  * `Bin_Q`: 任意の単位でのビンニングのための量
  * `Weights`: マップのための重み
  * `center`: 物理コード単位で外向きに投影している位置
  * `radius_limits`: マッピングすべきシェルの内半径と外半径
  * `Nside`: healpixマップのNside、2の累乗でなければならない
  * `calc_mean`: 視線に沿った平均を計算します。`false`に設定すると、`Bin_Q > 0`の粒子のみがマップに寄与します。
  * `show_progress`: 進捗バーを表示します
  * `output_from_all_workers`: 複数のワーカーからの出力を許可します。`false`に設定すると、メインプロセスのみが進捗バーを表示します。
