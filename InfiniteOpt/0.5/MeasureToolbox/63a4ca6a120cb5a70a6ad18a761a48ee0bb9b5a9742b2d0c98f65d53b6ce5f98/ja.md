```
@expect(expr::JuMP.AbstractJuMPScalar,
        prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef};
        [num_supports::Int = DefaultNumSupports, 
        kwargs...]
        )::GeneralVariableRef
```

[`expect`](@ref) の効率的なラッパーです。詳細についてはそのドキュメント文字列を参照してください。
