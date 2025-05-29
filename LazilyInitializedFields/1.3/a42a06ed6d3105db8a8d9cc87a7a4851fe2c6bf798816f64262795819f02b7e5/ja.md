```
@isinit a.b
```

オブジェクト `a` の遅延フィールド `b` が初期化されているかを確認します。`b` が `a` の遅延フィールドでない場合は `NonLazyFieldException` をスローします。マクロ版の [`isinit(a, :b)`](@ref)

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
