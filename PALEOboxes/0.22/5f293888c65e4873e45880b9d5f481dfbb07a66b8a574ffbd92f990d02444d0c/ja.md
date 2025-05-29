```
AbstractReaction
```

反応のための抽象基本型。

# 実装

派生型はフィールド `base::`[`ReactionBase`](@ref) を含むべきであり、通常は [`ParametersTuple`](@ref) を含むべきです。例えば、

```
Base.@kwdef mutable struct ReactionHello{P} <: PB.AbstractReaction
    base::PB.ReactionBase

    pars::P = PB.ParametersTuple(
        PB.ParDouble("my_par", 42.0, units="yr", 
            description="浮動小数点値のスカラー引数 'my_par' の例"),
    )

    some_additional_field::Float64   # ディスクから読み取ったデータをキャッシュするための追加フィールドなど
end
```

派生型は [`register_methods!`](@ref) を実装すべきであり、オプションで [`create_reaction`](@ref)、[`set_model_geometry`](@ref)、[`check_configuration`](@ref)、[`register_dynamic_methods!`](@ref) を実装することができます。

メソッドは [`add_method_setup!`](@ref)、[`add_method_initialize!`](@ref)、[`add_method_do!`](@ref) を使用して登録されるべきです。
