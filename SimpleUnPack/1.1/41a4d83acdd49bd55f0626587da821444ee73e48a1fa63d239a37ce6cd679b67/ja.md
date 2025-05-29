```
@unpack a, b, ... = x
```

`x`のプロパティ`a`、`b`、...を同じ名前の変数にデストラクトします。

このマクロの動作は、[Julia#39285](https://github.com/JuliaLang/julia/pull/39285)で導入された`(; a, b, ...) = x`と同等であり、Julia >= 1.7.0-DEV.364で利用可能です。

他にも[`@pack!`](@ref)、[`@unpack_fields`](@ref)、[`@pack_fields!`](@ref)を参照してください。
