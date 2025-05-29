入力生成セット（[`Stabilizer`](@ref））によって表される完全な安定器群を返します。

返されるオブジェクトは指数的に長くなります。

```jldoctest
julia> groupify(S"XZ ZX")
+ __
+ XZ
+ ZX
+ YY
```
