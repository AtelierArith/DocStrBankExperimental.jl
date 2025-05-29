```
constraint_by_name(stochasticprogram::StochasticProgram,
                   stage::Integer,
                   name::String)::Union{SPConstraintRef, Nothing}
```

`name`属性を持つ制約の参照を`stochasticprogram`の`stage`で返します。もしその名前属性を持つ制約がなければ`Nothing`を返します。複数の制約が`name`を名前属性として持つ場合はエラーをスローします。

```
constraint_by_name(stochasticprogram::StochasticProgram,
                   stage::Integer,
                   name::String,
                   F::Type{<:Union{AbstractJuMPScalar,
                                   Vector{<:AbstractJuMPScalar},
                                   MOI.AbstactFunction}},
                   S::Type{<:MOI.AbstractSet})::Union{SPConstraintRef, Nothing}
```

上記のメソッドと似ていますが、制約が`F`-in-`S`制約でない場合はエラーをスローします。ここで`F`はJuMPまたはMOIの関数の型で、`S`はMOIの集合の型です。
