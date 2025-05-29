```
@io2str ex
```

プレースホルダー `::IO` を新しく割り当てられた `Base.IOBuffer` に置き換え、その後文字列に変換して返します。

このマクロは、`IO` 引数を必要とするテキストベースの印刷機能を便利にテストするためのものです。特に一般的な例としては、カスタム `Base.show` メソッドがあります。

# 例

```julia-repl
julia> using ReferenceTests

julia> @io2str print(::IO, "Hello World")
"Hello World"

julia> @io2str show(IOContext(::IO, :limit=>true, :displaysize=>(10,10)), "text/plain", ones(5))
"5-element Array{Float64,1}:
 1.0
 1.0
 1.0
 1.0
 1.0"
```
