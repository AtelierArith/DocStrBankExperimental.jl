```julia
calcHelix_T(; ...)
calcHelix_T(t_start; ...)
calcHelix_T(t_start, t_stop; ...)
calcHelix_T(
    t_start,
    t_stop,
    pointsperturn;
    direction,
    T,
    radius,
    spine_t,
    xr_t,
    yr_t,
    h
)

```

"t軸"（すなわちz軸、z(t)=tと仮定）に沿った曲線によってパラメータ化された一般化されたヘリックスを生成します。  

ノート

  * （`t`、`x,y`、および`yaw`角度）のベクトルを返します。
  * 原点でt_startにオフセットし、+y軸に沿った方向を向いています。
  * コールバック`xr_t(t)`および`yr_t(t)`を使用して、任意の曲線でヘリックスを傾けます。例としては、

      * `xr_t = (t) -> (1/3)t`はx軸に沿ったヘリックスパターンを生成します。
      * または、xr*t、yr*tを使用してtに沿ったスパイラルを作成し、xy上にバラパターンを生成します。
      * より複雑なパターンのショートカットとして`spine_t(t)=xr_t(t) + im*yr_t(t)`を使用します。
      * `xr_t`および`yr_t`は`radius`という係数でスケーリングされているため、必要に応じて入力を除算でスケーリング解除します。
  * シミュレーションされた軌道とノイズのある軌道（すなわち、より簡単なガウス・マルコフ過程）のために関数を2回使用します。
  * 勾配（すなわち角度）計算は1e-8のオーダーです。

関連

[`RoME.generateGraph_Helix2D!`](@ref)
