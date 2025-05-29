```
@post function name ...
```

`name`への呼び出しを`other`への各呼び出しの後に挿入するマクロ`@name [[variable] variable ...] function other ...`を作成します。

`variable`は`name`に渡される変数名を定義します。`variable`が省略された場合、`name`は`other`の戻り値に対して呼び出されます。`variable`が使用される場合、`other`の各`return`の前に呼び出しが挿入されるか、存在しない場合は`other`の最後の式として挿入されます。複数の変数が与えられた場合、`name`はそれぞれに対して呼び出されます。例えば：

  * `@name x y z`は`@name x @name y @name z`の短縮表記であり、`name(x)`, `name(y)`, `name(z)`を呼び出します。
  * `@name x,y,z`は`name(x,y,z)`を呼び出します。

# 例

```jldoctest
julia> @post function nonzero(x::Int)
           @assert x!=0
       end
@nonzero (macro with 2 methods)

julia> @nonzero function foo(x::Int,y::Int)
           x*y
       end
foo (generic function with 1 method)

julia> foo(1,2)
2

julia> foo(1,0)
ERROR: AssertionError: x != 0

julia> @nonzero @nonzero a function foo(x::Int,y::Int)
           a = x-1
           return a*y
       end
foo (generic function with 1 method)

julia> foo(1,2)
ERROR: AssertionError: x != 0
```

`a`はゼロであってはならないため失敗します

```jldoctest
julia> foo(2,2)
2

julia> foo(2,0)
ERROR: AssertionError: x != 0
```

戻り値はゼロであってはならないため失敗します
