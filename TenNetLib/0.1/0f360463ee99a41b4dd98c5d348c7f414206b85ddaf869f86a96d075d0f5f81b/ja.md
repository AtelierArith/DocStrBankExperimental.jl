```
function OptimizeParamsTTN(;maxdim::Vector{Int}, nsweeps::Vector{Int}, 
                           cutoff::Union{Vector{Float64}, Float64} = Float64_threshold(),
                           noise::Union{Vector{Float64}, Float64, Int} = 0.0,
                           noisedecay::Union{Vector{Float64}, Float64, Int} = 1.0,
                           disable_noise_after::Union{Vector{Int}, Int} = typemax(Int))
```

`OptimizeParamsTTN`のコンストラクタ。名前付き引数を取ります。

  * `maxdim::Vector{Int}`: 最適化の各段階で許可される最大TTNボンド/リンク次元。
  * `nsweeps::Vector{Int}`: 最適化の各段階で実行されるスイープの数。
  * `cutoff::Union{Float64, Vector{Float64}} = Float64_threshold()`: 最適化の各段階でのSVD切断のカットオフ。`Float64`の場合、`cutoff`は最適化シミュレーション全体で同じままです。
  * `noise::Union{Float64, Int, Vector{Float64}} = 0.0`: 最適化の各段階でのノイズレベル。`Float64` / `Int`の場合、初期の`noise`は最適化全体で同じままです。
  * `noisedecay::Union{Float64, Int, Vector{Float64}} = 1.0`: 最適化の各段階でのノイズレベルの減衰。ノイズは各スイープ後に`noisedecay`で割られます。`Float64` / `Int`の場合、`noisedecay`はDMRGシミュレーション全体で同じままです。
  * `disable_noise_after::Union{Int, Vector{Int}} = typemax(Int)`: 最適化の各段階でこのスイープ数後にノイズをオフにします。`Int`の場合、`disable_noise_after`は最適化全体で同じままです。
