```
macro add_init(symbol::Symbol)

辞書とjsonを使用してオブジェクトを構築するための構築メソッドをDataTypeに自動的に追加し、base.@kwdefによって修正されたDataTypeに適応します。
```

# 例:

```julia
    @Base.kwdef struct Test
        a::Int
        b::Int=2
        c::Int
    end
    @add_init Test

    Test(Dict("a"=>1, "c"=>3)) == Test(1,2,3)
```
