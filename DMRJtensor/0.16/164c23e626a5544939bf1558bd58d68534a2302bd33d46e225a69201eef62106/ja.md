```
heisenbergMPO(i[,spinmag=0.5,J=0.5,Ops=spinOps(spinmag)])
```

均一結合 `J`、スピンの大きさ `spinmag`、および演算子セット `Ops` のためのハイゼンベルグモデルのバルクMPOを作成します。

#例:   julia> En = Vector{Float64}(undef,8)   julia> for Ns = 3:10            mpo = makeMPO(XXZ,2,Ns)            psi = randMPS(2,Ns)            En[Ns-2] = dmrg(psi,mpo,sweeps=50,m=100,cutoff=1E-9)          end

#期待される出力:   3 -1.0   4 -0.9571067811865475   5 -1.9278862533179937   6 -2.0019953568985334   7 -2.836239680686649   8 -3.3749325986878933   9 -3.7363216980340077   10 -4.258035204636598

参照: [`XXZ`](@ref)
