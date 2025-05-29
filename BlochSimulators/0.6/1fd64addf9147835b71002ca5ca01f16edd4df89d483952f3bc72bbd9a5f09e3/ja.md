```
simulate_signal(resource, sequence, parameters, trajectory, coil_sensitivities)
```

時間点 `t` におけるコイル `i` からのMR信号を次のようにシミュレートします: `sᵢ(t) = ∑ⱼ cᵢⱼρⱼmⱼ(t)`。ここで、`cᵢⱼ` はボクセル `j` の位置におけるコイル `i` の感度、`ρⱼ` はボクセル `j` のプロトン密度、`mⱼ(t)` はBlochシミュレーションを通じて得られたボクセル `j` の（正規化された）横磁化です。

# 引数

  * `resource::AbstractResource`: `CPU1()`, `CPUThreads()`, `CPUProcesses()` または `CUDALibs()` のいずれか
  * `sequence::BlochSimulator`: カスタムシーケンス構造体
  * `parameters::SimulationParameters`: 各ボクセルの組織特性を持つ配列
  * `trajectory::AbstractTrajectory`: カスタム軌道構造体
  * `coordinates::StructArray{<:Coordinates}`: 各ボクセルの空間座標を持つ配列
  * `coil_sensitivities::AbstractMatrix`: ボクセル `v` におけるコイル `j` の感度は `coil_sensitivities[v,j]` で与えられます

# 戻り値

  * `signal::AbstractArray{<:Complex}`: `sequence` と `trajectory` に対するシミュレートされたMR信号。配列のサイズは（# 読み出しごとのサンプル数, # 読み出し, # コイル）です。
