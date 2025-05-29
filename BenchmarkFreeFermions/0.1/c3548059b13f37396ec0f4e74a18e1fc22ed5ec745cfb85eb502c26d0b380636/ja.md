```
 EigenModes(Tij::AbstractMatrix{F}) -> ϵ::Vector{Float64}, V::Matrix{F}
```

ホッピング行列 `Tij = - V diagm(ϵ) V'` を数値的に対角化して、単一粒子スペクトル `ϵ` と固有ベクトル `V` を得ます。慣習として、`H = - \sum_ij Tij c_i^dag c_j` であり、分離されたハミルトニアンは `H = \sum_k ϵ_k f_k^dag f_k` と読み取られ、ここで `c_i = \sum_k V[i,k] f_k` です。
