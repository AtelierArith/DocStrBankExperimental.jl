```
magnetization_to_signal(::Union{CPU1,CPUThreads,CUDALibs}, magnetization, parameters, trajectory::CartesianTrajectory2D, coordinates, coil_sensitivities)
```

# 引数

  * `magnetization`:          サイズ (# readouts, # voxels) の Matrix{Complex} で、エコー時間での位相エンコードされた磁化。
  * `parameters`:     空間座標を含むすべてのボクセルの組織パラメータ。
  * `trajectory`:     カルテジアン軌道構造体。
  * `coordinates`:    各ボクセルの空間座標を持つ Vector{Coordinates}。
  * `coil_sensitivities`:     サイズ (# voxels, # coils) の Matrix{Complex} で、コイル感度。

# 戻り値

  * `signal`: 長さ (# coils) のベクトルで、各要素はサイズ (# readouts, # samples per readout) の Matrix{Complex}。

# 拡張ヘルプ

simulate_signal 関数の説明に記載されているように（`src/simulate/signal.jl`を参照）、コイル `i` からの時間点 `t` での MR 信号を次のようにシミュレートします: signalᵢ[t] = sum(m[t,v] * cᵢ[v] * ρ[v]  for v in 1:(# voxels))。ここで `cᵢ` はコイル `i` のコイル感度プロファイル、`ρ` はプロトン密度マップ、`m` は各ボクセルのすべての時間点での磁化を含む行列です。

各コイルの出力 (signalᵢ) は原則として長さ (# samples per readout) * (# readouts) の `Vector{Complex}` です。出力をサイズ (# samples per readout, # readouts) の `Matrix{Complex}` に再形成し、`m` に対しても同様のことを行うと、r 番目の読み出しの s 番目のサンプルポイントに関連する信号値は signalᵢ[r,s] = sum( m[r,s,v] * cᵢ[v] * ρ[v]  for v in 1:(# voxels)) と表現できます。

ここでの問題は、通常、完全な m を保存できないことです。代わりに、エコー時間での磁化のみを計算します。その理由は、mᵣ があるボクセルの r 番目のエコー時間での磁化であり、E = exp(-Δt*R₂[v]) * exp(im*(Δkₓ*x[v])) がサンプルポイントごとの変化である場合（カルテジアンシーケンスではすべての読み出しとサンプルで同じ）、エコー時間に対する s 番目のサンプルの磁化は mₛ = mᵣ * E[v]^s と計算できるからです。

したがって、次のように書くことができます。

signalⱼ[r,s] = sum( magnetization[r,v] * E[v]^s * ρ[v] * cⱼ[v] for v in 1:(# voxels)) signalⱼ[r,s] = magnetization[r,:] * (E.^s .* ρ .* cⱼ)

(E.^s .* ρ .* cⱼ) 部分はすべての読み出しで同じであるため、この計算をすべての読み出しに対して同時に行うことができます: signalⱼ[:,s] = magnetization * (E.^s .* ρ .* cⱼ)

行列 Eˢ を E .^ (-(ns÷2):(ns÷2)-1) と定義すると、異なるサンプルポイントの計算も単一の行列-行列乗算を使用して同時に行うことができます: signalⱼ = magnetization * (Eˢ .* (ρ .* cⱼ))

signalⱼ 配列のサイズは (# readouts, # samples per readout) です。転置された形で持つことを好むため、signalⱼ = transpose(Eˢ .* (ρ .* cⱼ)) * transpose(magnetization) を計算します。

最終出力のために、各コイル j に対してこの計算を行い、結果として信号行列のベクトル（各コイルのための1つの行列）を得ます。

この実装は完全にベクトル化されたコードに依存しており、CPU と GPU の両方で動作します。行列-行列の乗算は - 私の考えでは - すでにマルチスレッド化されているため、別のマルチスレッド実装は必要ありません。
