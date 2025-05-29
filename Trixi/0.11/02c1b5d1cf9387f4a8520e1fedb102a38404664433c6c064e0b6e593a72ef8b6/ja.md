```
EulerAcousticsCouplingCallback
```

!!! warning "実験的なコード"
    このコールバックは実験的であり、将来のリリースで変更される可能性があります。


音響摂動方程式と圧縮性オイラー方程式を結合するコールバックです。 [`SemidiscretizationEulerAcoustics`](@ref) と併用する必要があります。このコールバックは流れソルバーを管理し、常に音響ソルバーよりも1つのタイムステップ先にあり、各タイムステップ後に音響ソース項を計算します。線形化されたラムベクトルがソース項として使用されます。すなわち、

$$
\mathbf{s} = -(\mathbf{\omega'} \times \bar{\mathbf{v}}
  + \bar{\mathbf{\omega}} \times \mathbf{v'}),
$$

ここで、$\mathbf{v}$ は速度を、$\mathbf{\omega}$ は渦度を示し、バー $\bar{(\cdot)}$ は時間平均量を示します（[`AveragingCallback`](@ref) を参照）およびプライム $(\cdot)'$ は $\phi' = \phi - \bar{\phi}$ によって定義される摂動量を示します。ここでの摂動量は純粋な流れ解に完全に基づいており、音響摂動方程式の状態変数と混同しないでください。

さらに、このコールバックは両方のソルバーのタイムステップサイズを管理し、[`AveragingCallback`](@ref) を使用して得られた結果を用いて音響摂動方程式の平均値を初期化します。

  * Michael Schlottke-Lakemper (2017) エアロアコースティック分析のための直接ハイブリッド法 [DOI: 10.18154/RWTH-2017-04082](https://doi.org/10.18154/RWTH-2017-04082)
