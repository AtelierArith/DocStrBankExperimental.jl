```
@uninit! f.b
```

オブジェクト `f` のフィールド `b` を初期化解除します。`b` が `a` の遅延フィールドでない場合は `NonLazyFieldException` をスローします。マクロ版の [`uninit`](@ref)

```jldoctest
julia> @lazy struct Foo
           @lazy b::Int
       end

julia> f = Foo(uninit)
Foo(uninit)

julia> @isinit f.b
false

julia> @init! f.b = 5
5

julia> @isinit f.b
true
```
