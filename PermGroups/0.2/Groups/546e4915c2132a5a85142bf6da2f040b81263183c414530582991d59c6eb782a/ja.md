`@GapObj struct...`

`GapObj`は、要求されたときにプロパティがオンデマンドで計算されるオブジェクトの一種です。したがって、固定フィールドを持っていますが、動的に新しいフィールドを持つことができます。固定フィールドへのアクセスは、任意の`struct`のフィールドと同じくらい効率的です。動的フィールドへのアクセスは、`Dict`のルックアップの時間がかかります。

```julia_repl
julia> @GapObj struct Foo
       a::Int
       end

julia> s=Foo(1,Dict{Symbol,Any}())
Foo(1, Dict{Symbol, Any}())

julia> s.a
1

julia> haskey(s,:b)
false

julia> s.b="hello"
"hello"

julia> haskey(s,:b)
true

julia> s.b
"hello"
```

動的フィールドは、`G`のフィールド`.prop`に格納されており、これは`Dict{Symbol, Any}()`型です。これがコンストラクタで必要な追加の引数を説明しています。この名前はGAPレコードを模倣しているためですが、もしかしたらより良い名前があるかもしれません。`GapObj`がそのフィールド`prop`から継承するメソッドは、`haskey`、`getindex`、`delete!`、および`get!`です。
