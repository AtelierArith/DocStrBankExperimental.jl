```
SHAKE_RATTLE(constraints, n_atoms, dist_tolerance, vel_tolerance)
```

SHAKEおよびRATTLEアルゴリズムを使用してシミュレーション中に距離を制約します。

速度制約は、[`VelocityVerlet`](@ref)のような速度を統合するシミュレーターに対して課されます。SHAKEについては[Ryckaert et al. 1977](https://doi.org/10.1016/0021-9991(77)90098-5)、RATTLEについては[Andersen 1983](https://doi.org/10.1016/0021-9991(83)90014-1)、RATTLEアルゴリズムを満たすために解決される線形システムの導出については[Elber et al. 2011](https://doi.org/10.1140%2Fepjst%2Fe2011-01525-9)を参照してください。

現在、GPUシミュレーションには対応していません。

# 引数

  * `constraints`: システムに課される制約のベクトル。
  * `n_atoms::Integer`: システム内の原子の数。
  * `dist_tolerance`: 位置制約を計算する際に反復手続きを終了するために使用される許容誤差で、座標と同じ単位である必要があります。
  * `vel_tolerance`: 速度制約を計算する際に反復手続きを終了するために使用される許容誤差で、速度と座標の同じ単位である必要があります。
