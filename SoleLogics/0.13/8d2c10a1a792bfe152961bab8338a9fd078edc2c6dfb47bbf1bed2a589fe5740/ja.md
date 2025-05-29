```
parseformula(
    [F::Type{<:Formula}=SyntaxTree],
    expr::AbstractString,
    additional_operators::Union{Nothing,AbstractVector} = nothing;
    kwargs...
)::F

parseformula(
    F::Type{<:SyntaxTree},
    expr::AbstractString,
    logic::AbstractLogic;
    kwargs...
)::F
```

文字列式（その[`syntaxstring`](@ref)）から型`F`の数式を解析します。

デフォルトでは、この関数は[`SoleLogics.BASE_PARSABLE_CONNECTIVES`](@ref)（例：¬、∧、∨、→）の演算子のみを解析できます。追加の非標準演算子はベクトル`additional_operators`として提供でき、その`syntaxstring`sが解析に使用されます。`syntaxstring`sが衝突する場合、提供された追加演算子が標準のものを上書きします。

`SyntaxTree`sを解析する際には、[シュンティングヤード](https://en.wikipedia.org/wiki/Shunting_yard_algorithm)アルゴリズムが使用され、このメソッドは以下のキーワード引数を許可します。

# キーワード引数

  * `function_notation::Bool = false`: `true`に設定すると、式は関数表記（例：`"⨁(arg1, arg2)"`）として扱われます。それ以外の場合、[中置表記](https://en.wikipedia.org/wiki/Infix_notation)（例：`"arg1 ⨁ arg2"`）として扱われます。
  * `atom_parser::Base.Callable = Atom{String}`: 式内で認識された後に原子を解析するために使用される呼び出し可能な関数です。原子を返すか、`Atom`自体を返す必要があります。
  * `additional_whitespaces::Vector{Char} = Char[]`: 各構文トークンから削除される文字です。たとえば、`'@' in additional_whitespaces`の場合、"¬@p@"は"¬p"として解析されます。
  * `opening_parenthesis::String = "("`: 式ブロックの開始を示す文字列です。
  * `closing_parenthesis::String = ")"`: 式ブロックの終了を示す文字列です。
  * `arg_delim::String = ","`: `function_notation = true`の場合、関数呼び出しの異なる引数を区切る文字列です。

!!! 警告     正常に機能するためには、任意の構文トークンの`syntaxstring`は空白で接頭辞または接尾辞を付けることができません。たとえば、任意の演算子`⨁`について、`syntaxstring(⨁) == strip(syntaxstring(⨁))`が成り立つ必要があります。また、`syntaxstring`sには特別な記号（`opening_parenthesis`、`closing_parenthesis`、および`arg_delim`）を部分文字列として含めることはできません。

# 例

```julia-repl
julia> syntaxstring(parseformula("¬p∧q∧(¬s∧¬z)"))
"¬p ∧ q ∧ ¬s ∧ ¬z"

julia> syntaxstring(parseformula("∧(¬p,∧(q,∧(¬s,¬z)))", function_notation=true))
"¬p ∧ q ∧ ¬s ∧ ¬z"

julia> syntaxstring(parseformula("¬1→0"; atom_parser = (x -> Atom{Float64}(parse(Float64, x)))))
"(¬1.0) → 0.0"
```

!!! 注     任意の`Formula`型`F`について、この関数は[`syntaxstring`](@ref)の逆であるべきです。すなわち、もし`φ::F`であれば、次のことが成り立つべきです。少なくともいくつかの`args`に対して、すべての`kwargs`が正しい解析を許可する場合：`φ == parseformula(F, syntaxstring(φ, args...; kwargs...), args...; kwargs...)`。

他に[`SyntaxTree`](@ref)、[`BASE_PARSABLE_CONNECTIVES`](@ref)、[`syntaxstring`](@ref)を参照してください。
