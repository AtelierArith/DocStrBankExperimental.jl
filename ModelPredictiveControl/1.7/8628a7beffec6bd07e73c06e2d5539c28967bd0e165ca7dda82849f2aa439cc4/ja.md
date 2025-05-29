抽象スーパタイプ [`LinModel`](@ref) と [`NonLinModel`](@ref) タイプの。

---

```
(model::SimModel)(d=[]) -> y
```

呼び出し可能な `SimModel` オブジェクトを [`evaloutput`](@ref) のエイリアスとして使用するファンクター。

# 例

```jldoctest
julia> model = NonLinModel((x,u,_,_)->-x + u, (x,_,_)->x .+ 20, 4, 1, 1, 1, solver=nothing);

julia> y = model()
1-element Vector{Float64}:
 20.0
```
