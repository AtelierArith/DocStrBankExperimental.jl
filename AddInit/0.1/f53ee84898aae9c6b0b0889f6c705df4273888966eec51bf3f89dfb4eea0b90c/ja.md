```
macro add_init(type::Expr)

辞書とJSONを使用してオブジェクトを構築するためのコンストラクタをDataTypeに自動的に追加します
```

# 例:

```julia
    @add_init struct Test
        field:AbstractString
    end

    Test("{"field":"a"}") == Test("a")
    Test(Dict("field"=>"a")) == Test("a")
```
