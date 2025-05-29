```
mutable struct JLStruct <: JLExpr
```

タイプはJuliaの構造体を説明します。

```
JLStruct(;kw...)
```

`JLStruct`インスタンスを作成します。

# 利用可能なフィールドとキーワード引数

以下のすべてのフィールドは、コンストラクタのキーワード引数`kw`として有効であり、`<object>.<field>`を介してアクセスできます。

コンストラクタに必要な唯一のキーワード引数は`name`であり、残りはすべてオプションです。

  * `name::Symbol`: 構造体の名前、これは唯一の必須キーワード引数です。
  * `ismutable::Bool`: 構造体定義が可変かどうか。
  * `typevars::Vector{Any}`: 構造体の型変数、`Symbol`または`Expr`である必要があります。
  * `supertype`: 構造体定義のスーパークラス。
  * `fields::Vector{JLField}`: 構造体のフィールド定義、[`JLField`](@ref)である必要があります。
  * `constructors::Vector{JLFunction}`: 構造体のコンストラクタ定義、[`JLFunction`](@ref)である必要があります。
  * `line::LineNumberNode`: エラーレポートなどのための定義位置を示す`LineNumberNode`。
  * `doc::String`: 構造体のドキュメンテーション文字列。
  * `misc`: 構造体本体内で発生するその他の事柄、定義上、これは単に通過し、構造体本体の外でそれらを評価するのと同等です。

# 例

Juliaの構造体を構築します。

```julia
julia> JLStruct(;name=:Foo, typevars=[:T], fields=[JLField(;name=:x, type=Int)])
struct Foo{T}
    x::Int64
end
```

Juliaの構造体式を分解します。

```julia
julia> ex = :(struct Foo{T}
           x::Int64
       end)
:(struct Foo{T}
      #= REPL[31]:2 =#
      x::Int64
  end)

julia> jl = JLStruct(ex)
struct Foo{T}
    #= REPL[31]:2 =#
    x::Int64
end
```

Juliaの構造体式を生成します。

```julia
julia> codegen_ast(jl)
:(struct Foo{T}
      #= REPL[31]:2 =#
      x::Int64
  end)
```
