```
function DMRGParams(;maxdim::Vector{Int}, nsweeps::Vector{Int}, 
                    cutoff::Union{Vector{Float64}, Float64, Int} = _Float64_Threshold,
                    noise::Union{Vector{Float64}, Float64, Int} = 0.0,
                    noisedecay::Union{Vector{Float64}, Float64, Int} = 1.0,
                    disable_noise_after::Union{Vector{Int}, Int} = typemax(Int))
```

`DMRGParams`のコンストラクタ。名前付き引数のみを受け取ります。

  * `maxdim::Vector{Int}`: DMRGの各段階で許可される最大MPSボンド/リンク次元。
  * `nsweeps::Vector{Int}`: DMRGの各段階で実行されるスイープの数。
  * `cutoff::Union{Int, Float64, Vector{Float64}} = Float64_threshold()`: DMRGの各段階でのSVD切り捨てのカットオフ。`Float64`の場合、`cutoff`はDMRGシミュレーション全体で同じままです。
  * `noise::Union{Float64, Int, Vector{Float64}} = 0.0`: DMRGの各段階でのノイズレベル。`Float64`または`Int`の場合、初期の`noise`はDMRGシミュレーション全体で同じままです。
  * `noisedecay::Union{Float64, Int, Vector{Float64}} = 1.0`: DMRGの各状態でのノイズレベルの減衰。各スイープの後にノイズは`noisedecay`で割られます。`Float64`または`Int`の場合、`noisedecay`はDMRGシミュレーション全体で同じままです。
  * `disable_noise_after::Union{Int, Vector{Int}} = typemax(Int)`: DMRGの各状態でこのスイープ数の後にノイズをオフにします。`Int`の場合、`disable_noise_after`はDMRGシミュレーション全体で同じままです。
