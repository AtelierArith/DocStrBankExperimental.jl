```
WrapperSurface{T,S<:Surface{T}} <: Surface{T}
```

カスタム[`OpticalInterface`](@ref)サブクラスのための[`Surface`](@ref)の拡張の基盤となる汎用サーフスタイプです。本質的には、`WrapperSurface`のフィールドである`surface`にすべての`Surface`および`ParametricSurface`メソッドを転送します。また、基盤となるサーフェスとの交差をテストし、[`EmptyInterval`](@ref)または半空間（決して閉じた区間ではない）を返す[`surfaceintersection`](@ref)の汎用実装も提供します。
