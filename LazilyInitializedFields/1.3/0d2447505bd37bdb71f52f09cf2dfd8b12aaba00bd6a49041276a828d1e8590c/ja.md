```
@init! a.b = v
```

オブジェクト `a` の遅延フィールド `b` を `v` に初期化します。`b` が `a` の遅延フィールドでない場合は `NonLazyFieldException` をスローします。`b` がすでに初期化されている場合は `AlreadyInitializedException` をスローします。マクロ版の `init!(a, :b, v)`

```jldoctest
julia> @lazy struct Foo
           @lazy b::Int
       end

julia> f = Foo(uninit)
Foo(uninit)

julia> f.b
ERROR: field `b` in struct of type `Foo` is not initialized
[...]

julia> @init! f.b = 3
3

julia> f.b
3

julia> @init! f.b = 2
ERROR: field `b` in struct of type `Foo` already initialized
[...]
```
