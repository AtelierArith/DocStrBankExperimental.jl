遅延初期化フィールドを扱うためのパッケージ。

### エクスポート:

  * マクロ: `@lazy`, `@init!`, `@uninit!`, `@isinit`.
  * 関数: `init!` `uninit!`, `isinit`, `islazyfield`.
  * オブジェクト: `uninit`.
  * 例外: `NonLazyFieldException`, `UninitializedFieldException`, `AlreadyInitializedException`

### 使用例:

```julia-repl
julia> @lazy struct Foo{T}
           a::T
           @lazy b::Int
           @lazy c::Union{Float64, Nothing}
           @lazy d::Union{Int, Nothing}
           e::Float64
       end

julia> f = Foo(2, uninit, 2.0, nothing, 3.0)
Foo{Int64}(2, uninit, 2.0, nothing, 3.0)

julia> @isinit f.b
false

julia> @isinit f.c
true

julia> f.b
ERROR: field `b` in struct of type `Foo{Int64}` is not initialized
[...]

julia> @init! f.b = 4
4

julia> f.b
4

julia> @init! f.a=2
ERROR: field `a` in struct of type `Foo{Int64}` is not lazy, lazy fields are `b` ,`c` ,`d`.
[...]

julia> @uninit! f.b
uninit

julia> @isinit f.b
false
```
