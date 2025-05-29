```
sinkhorn(a::Union{PyObject, Array{Float64}}, b::Union{PyObject, Array{Float64}}, M::Union{PyObject, Array{Float64}};
reg::Float64 = 1.0, iter::Int64 = 1000, tol::Float64 = 1e-9, method::String="sinkhorn")
```

Sinkhornアルゴリズムを用いて最適輸送を計算します。数学的な定式化は次の通りです。

$$
\begin{aligned}
\arg\min_P &\ \left(P, M\right) + \lambda \Omega(\Gamma)\\ 
\text{s.t.} &\ \Gamma 1 = a\\ 
&\ \Gamma^T 1 = b\\ 
& \Gamma \geq 0 
\end{aligned}
$$

ここで$\Omega$はエントロピー正則化です。$\lambda$が非常に小さい場合、アルゴリズムは数値的不安定性に直面する可能性があります。

実装はhttps://github.com/rflamary/POTから適応されています。  
