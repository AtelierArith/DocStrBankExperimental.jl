```
mutable struct JLFunction <: JLExpr
JLFunction(;kw...)
```

TypeはJuliaの関数宣言式を表します。

# フィールドとキーワード引数

以下のすべてのフィールドは、コンストラクタのキーワード引数`kw`として有効であり、`<object>.<field>`を介してアクセスできます。

コンストラクタに必要な唯一のキーワード引数は`name`であり、残りはすべてオプションです。

  * `head`: オプション、関数のヘッダー、`:function`、`:(=)`、または`:(->)`を指定できます。
  * `name`: オプション、関数名、`Nothing`、`Symbol`、または`Expr`の型を持つことができ、デフォルトは`nothing`です。
  * `args`: オプション、関数の引数、`Expr`または`Symbol`のリストです。
  * `kwargs`: オプション、関数のキーワード引数、`Expr(:kw, name, default)`のリストです。
  * `rettype`: オプション、関数の明示的な戻り値の型、`Type`、`Symbol`、`Expr`、または単に`nothing`であり、デフォルトは`nothing`です。
  * `generated`: オプション、これが生成された関数かどうか。
  * `whereparams`: オプション、型変数、`Type`、`Expr`、または`nothing`のリストであり、デフォルトは`nothing`です。
  * `body`: オプション、関数の本体、`Expr`であり、デフォルトは`Expr(:block)`です。
  * `line::LineNumberNode`: 行情報を示す`LineNumberNode`です。
  * `doc::String`: この定義のドキュメント文字列です。

# 例

関数式を構築する

```julia
julia> JLFunction(;name=:foo, args=[:(x::T)], body= quote 1+1 end, head=:function, whereparams=[:T])
function foo(x::T) where {T}
    #= REPL[25]:1 =#    
    1 + 1    
end
```

関数式を分解する

```julia
julia> ex = :(function foo(x::T) where {T}
           #= REPL[25]:1 =#    
           1 + 1    
       end)
:(function foo(x::T) where T
      #= REPL[26]:1 =#
      #= REPL[26]:3 =#
      1 + 1
  end)

julia> jl = JLFunction(ex)
function foo(x::T) where {T}
    #= REPL[26]:1 =#    
    #= REPL[26]:3 =#    
    1 + 1    
end
```

`JLFunction`から`Expr`を生成する

```julia
julia> codegen_ast(jl)
:(function foo(x::T) where T
      #= REPL[26]:1 =#
      #= REPL[26]:3 =#
      1 + 1
  end)
```
