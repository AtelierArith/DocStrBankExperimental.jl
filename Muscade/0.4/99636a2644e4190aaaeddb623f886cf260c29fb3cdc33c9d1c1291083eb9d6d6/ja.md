```
X = variate{P,N}(x)
```

ここで `typeof(x)<:SVector{N}` の場合、優先度 `P` の自動微分オブジェクトの `SVector` を作成します。    

```
X = variate{P}(x)
```

ここで `typeof(x)<:Real` の場合、優先度 `P` のオブジェクトを作成します。    

参照: [`constants`](@ref), [`δ`](@ref), [`value`](@ref), [`∂`](@ref), [`VALUE`](@ref), [`value_∂`](@ref)
