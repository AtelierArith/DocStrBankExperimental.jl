```
choimatrix(circuit::Vector{<:Any}; kwargs...) =
choimatrix(sites::Vector{<:Index}, circuit::Vector{<:Any}; kwargs...)
choimatrix(sites::Vector{<:Index}, circuit_tensors::Vector{<:ITensor};
           full_representation = false,kwargs...)
```

ノイズのあるチャネルのためのチョイ行列を計算します

$$
\Lambda = (1+\mathcal{E})|\Phi\rangle\langle\Phi|^{\otimes n}
$$

`full_representation = true` の場合、近似なしで収束が行われ、出力オブジェクトのサイズは $n$ に対して指数関数的にスケールします。
