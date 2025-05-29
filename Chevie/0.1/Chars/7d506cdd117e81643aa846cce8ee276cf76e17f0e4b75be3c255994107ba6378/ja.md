`fakedegree(W, φ, q=Pol())`

は、反射群 `W` のパラメータ φ のキャラクターの擬似次数（定義については [`fakedegrees`](@ref) を参照）を返し、`q` で評価されます。

```julia-repl
julia> fakedegree(coxgroup(:A,2),[[2,1]],Pol(:q))
Pol{Int64}: q²+q
```
