```
mutable struct OptimizeParamsTTN
    maxdim::Vector{Int}
    nsweeps::Vector{Int}
    cutoff::Vector{Float64}
    noise::Vector{Float64}
    noisedecay::Vector{Float64}
    disable_noise_after::Vector{Int}
end
```

TTNの最適化スイープを制御するためのパラメータを保持します。

  * `maxdim::Vector{Int}`: 最適化の各段階で許可される最大TTNボンド/リンク次元。
  * `nsweeps::Vector{Int}`: 最適化の各段階で実行されるスイープの数。
  * `cutoff::Vector{Float64}`: 最適化の各段階でのSVD切断のカットオフ。
  * `noise::Vector{Float64}`: 最適化の各段階でのノイズレベル。
  * `noisedecay::Vector{Float64}`: 最適化の各段階でのノイズレベルの減衰。

ノイズは各スイープの後に`noisedecay`で割られます。

  * `disable_noise_after::Vector{Int}`: 最適化の各段階でこの数のスイープの後にノイズを無効にします。

これらの`Vector`はすべて同じ次元でなければなりません。
