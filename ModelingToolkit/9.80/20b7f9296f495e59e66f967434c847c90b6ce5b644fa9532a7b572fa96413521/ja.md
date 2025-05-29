```julia
equations(sys::ModelingToolkit.AbstractSystem) -> Any

```

システム `sys` とそのサブシステムのフラット化された方程式を取得します。これには、観測可能なもののいくつかの省略形やエイリアスが含まれる場合があります。システムの方程式を検査する最も便利な方法であることが多いです。

[`full_equations`](@ref) および [`ModelingToolkit.get_eqs`](@ref) も参照してください。
