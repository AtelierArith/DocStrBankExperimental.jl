```
syntaxstring(s::Syntactical; kwargs...)::String
```

任意の構文オブジェクト（例：`Formula`、`SyntaxTree`、`SyntaxToken`、`Atom`、`Truth`など）の文字列表現を返します。この表現は冗長な括弧を導入する可能性があることに注意してください。`kwargs`は、特定の条件下で構文トークン/ツリーを表示する方法を指定するために使用できます。

現在サポートされている`kwargs`は次のとおりです：

  * `function_notation = false::Bool`：`true`に設定すると、二項演算子の関数表記を強制します（[こちら](https://en.wikipedia.org/wiki/Infix_notation)を参照）。
  * `remove_redundant_parentheses = true::Bool`：`false`に設定すると、各構文要素が括弧で囲まれた構文文字列を印刷します。
  * `parenthesize_atoms = !remove_redundant_parentheses::Bool`：`true`に設定すると、原子（これは式の木構造の葉です）が括弧で囲まれることを強制します。

# 例

```julia-repl
julia> syntaxstring(parseformula("p∧q∧r∧s∧t"))
"p ∧ q ∧ r ∧ s ∧ t"

julia> syntaxstring(parseformula("p∧q∧r∧s∧t"), function_notation=true)
"∧(∧(∧(∧(p, q), r), s), t)"

julia> syntaxstring(parseformula("p∧q∧r∧s∧t"), remove_redundant_parentheses=false)
"((((p) ∧ (q)) ∧ (r)) ∧ (s)) ∧ (t)"

julia> syntaxstring(parseformula("p∧q∧r∧s∧t"), remove_redundant_parentheses=true, parenthesize_atoms=true)
"(p) ∧ (q) ∧ (r) ∧ (s) ∧ (t)"

julia> syntaxstring(parseformula("◊((p∧s)→q)"))
"◊((p ∧ s) → q)"

julia> syntaxstring(parseformula("◊((p∧s)→q)"); function_notation = true)
"◊(→(∧(p, s), q))"
```

他の情報としては、[`parseformula`](@ref)、[`SyntaxBranch`](@ref)、[`SyntaxToken`](@ref)があります。

# 実装

構文木の場合、`syntaxstring`は再帰関数であり、各ノードの構文子に対して自分自身を呼び出します。正しく機能するためには、`syntaxstring`は新しく定義されたすべての`SyntaxToken`（例：`SyntaxLeaf`、すなわち`Atom`および`Truth`値、`Operator`）に対して定義される必要があります。これは、*一意*の文字列表現を生成するようにしなければなりません。なぜなら、`Base.hash`および`Base.isequal`は、少なくとも`SyntaxTree`に関してはそれに依存しているからです。

特に、`Atom`の場合、関数はラップされた値に対して自分自身を呼び出します：

```
syntaxstring(a::Atom; kwargs...) = syntaxstring(value(a); kwargs...)
```

任意の値の`syntaxstring`はその`string`表現にデフォルト設定されていますが、適切な`syntaxstring`メソッドを定義することで定義できます。

!!! warning
    構文トークン（例：原子、演算子）の`syntaxstring`は、空白で接頭辞または接尾辞を付けるべきではありません。これは*解析*時に曖昧さを引き起こす可能性があります。同様の理由から、`syntaxstring`には括弧（`'('`、`')'`）を含めるべきではなく、関数表記で解析する際にはカンマ（`','`）も含めるべきではありません。


他の情報としては、[`SyntaxLeaf`](@ref)、[`Operator`](@ref)、[`parseformula`](@ref)があります。
