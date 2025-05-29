```julia
equations(sys::ModelingToolkit.AbstractSystem) -> Any

```

システム `sys` とそのサブシステムのフラット化された方程式を取得します。これには、観測可能な量のいくつかの省略形やエイリアスが含まれる場合があります。これは、システムの方程式を検査する最も便利な方法であることが多いです。

他にも [`full_equations`](@ref) と [`ModelingToolkit.get_eqs`](@ref) を参照してください。
