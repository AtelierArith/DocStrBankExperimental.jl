```julia
SimpleNoiseProcess{T, N, Tt, T2, T3, ZType, F, F2, inplace, RNGType} <:
AbstractNoiseProcess{T, N, Vector{T2}, inplace}
```

`NoiseProcess`と似ていますが、適応性のサポートがありません。これにより、軽量でわずかに高速になります。

!!! warn
    `SimpleNoiseProcess`は適応型SDEソルバーと一緒に使用すべきではありません。そうしないと、誤った結果が得られます。


```julia
SimpleNoiseProcess{iip}(t0, W0, Z0, dist, bridge;
    save_everystep = true,
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    reset = true, reseed = true) where {iip}
```

  * `t0`は最初の時間点です。
  * `W0`はプロセスの最初の値です。
  * `Z0`は擬似プロセスの最初の値です。これは高次のアルゴリズムに必要です。必要ない場合は、`nothing`に設定します。
  * `dist`は時間に沿ったステップの分布です。
  * `bridge`はブリッジング分布です。オプションですが、適応性と新しい値での補間には必要です。
  * `save_everystep`はブラウン運動のタイムシリーズのすべてのステップを保存するかどうかです。
  * `rng`はランダム数を生成するために使用されるローカルRNGです。
  * `reset`は各解決時にプロセスをリセットするかどうかです。
  * `reseed`は各解決時にプロセスを再シードするかどうかです。
