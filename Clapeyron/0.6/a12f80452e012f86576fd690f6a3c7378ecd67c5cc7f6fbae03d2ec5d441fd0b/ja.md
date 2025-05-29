```
PairParam{T}
```

ペアデータを含むために設計された構造体。基盤データストレージとして行列を使用します。

## 作成:

```julia-repl
julia> kij = PairParam("interaction params",["water","ammonia"],[0.1 0.0;0.1 0.0])
PairParam{Float64}(["water", "ammonia"]) with values:
2×2 Matrix{Float64}:
 0.1  0.0
 0.1  0.0
julia> kij.values
2×2 Matrix{Float64}:
 0.1  0.0
 0.1  0.0
julia> diagvalues(kij)
2-element view(::Vector{Float64}, 
1:3:4) with eltype Float64:
 0.1
 0.0
```

## モデルでの使用例:

```julia
#∑xᵢxⱼkᵢⱼを計算しましょう
function alpha(model,x)
    kij = model.params.kij.values
    ki = diagvalues(model.params.kij)
    res = zero(eltype(molarfrac))
    for i in @comps 
        @show ki[i] #対角値
        for j in @comps 
            res += x[i]*x[j]*kij[i,j]
        end
    end
    return res
end
```
