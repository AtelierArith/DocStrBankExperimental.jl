```
@pre function name ...
```

`name`への呼び出しを`other`への各呼び出しの前に挿入するマクロ`@name [[variable] variable ...] function other ...`を作成します。

`variable`は`name`に渡される変数名を定義します。`variable`が省略された場合、`name`の属性の名前が使用されます。複数の変数が指定された場合、`name`はそれぞれに対して呼び出されます。例えば：

  * `@name x y z`は`@name x @name y @name z`の短縮表記であり、`name(x)`, `name(y)`, `name(z)`を呼び出します。
  * `@name x,y,z`は`name(x,y,z)`を呼び出します。

# 例

```jldoctest
julia> @pre function nonzero(x::Int)
           @assert x!=0
       end
@nonzero (macro with 2 methods)

julia> @nonzero @nonzero y function foo(x::Int,y::Int)
           x+y
       end
foo (generic function with 1 method)
```

外側の`@nonzero`は、`nonzero`の関数定義により`x`を属性として使用します。

```jldoctest
julia> foo(1,2)
3

julia> foo(1,0)
ERROR: AssertionError: x != 0

julia> foo(0,1)
ERROR: AssertionError: x != 0
```
