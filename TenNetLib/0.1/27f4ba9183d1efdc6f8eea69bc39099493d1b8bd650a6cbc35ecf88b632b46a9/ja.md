```
mutable struct DMRGParams
    maxdim::Vector{Int}
    nsweeps::Vector{Int}
    cutoff::Vector{Float64}
    noise::Vector{Float64}
    noisedecay::Vector{Float64}
    disable_noise_after::Vector{Int}
end
```

DMRGスイープを制御するためのパラメータを保持します。

  * `maxdim::Vector{Int}`: DMRGの各ステージで許可される最大MPSボンド/リンク次元。
  * `nsweeps::Vector{Int}`: DMRGの各ステージで実行されるスイープの数。
  * `cutoff::Vector{Float64}`: DMRGの各ステージでのSVD切断のカットオフ。
  * `noise::Vector{Float64}`: DMRGの各ステージでのノイズレベル。
  * `noisedecay::Vector{Float64}`: DMRGの各ステージでのノイズレベルの減衰。ノイズは各スイープ後に`noisedecay`で割られます。
  * `disable_noise_after::Vector{Int}`: DMRGの各ステージでこの数のスイープ後にノイズをオフにするスイッチ。

これらの`Vector`はすべて同じ次元でなければなりません。
