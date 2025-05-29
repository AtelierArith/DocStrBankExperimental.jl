```
JLIfElse <: JLExpr
JLIfElse(;kw...)
```

`JLIfElse`は、Juliaの`if ... elseif ... else ... end`式を表します。この式は、条件とコードブロックをマップを介して挿入することで簡単に構築できます。

# フィールドとキーワード引数

以下のすべてのフィールドは、コンストラクタのキーワード引数`kw`として有効であり、`<object>.<field>`を介してアクセスできます。

  * `conds::Vector{Any}`: 条件の式。
  * `stmts::Vector{Any}`: 対応する条件の文の式。
  * `otherwise`: `else`本体。

# 例

### JLIfElseオブジェクトの構築

次のようにして`ifelse`を構築できます。

```julia
julia> jl = JLIfElse()
nothing

julia> jl[:(foo(x))] = :(x = 1 + 1)
:(x = 1 + 1)

julia> jl[:(goo(x))] = :(y = 1 + 2)
:(y = 1 + 2)

julia> jl.otherwise = :(error("abc"))
:(error("abc"))

julia> jl
if foo(x)
    x = 1 + 1
elseif goo(x)
    y = 1 + 2
else
    error("abc")
end
```

### Julia `Expr`オブジェクトの生成

対応する`Expr`オブジェクトを生成するには、[`codegen_ast`](@ref)を呼び出します。

```julia
julia> codegen_ast(jl)
:(if foo(x)
      x = 1 + 1
  elseif goo(x)
      y = 1 + 2
  else
      error("abc")
  end)
```
