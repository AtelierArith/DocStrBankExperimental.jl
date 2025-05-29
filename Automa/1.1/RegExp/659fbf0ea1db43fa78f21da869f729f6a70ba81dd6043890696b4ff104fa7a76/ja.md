```
RE(s::AbstractString)
```

入力バイトのシーケンスに一致するために使用されるオートマ正規表現（regex）。正規表現は、`@re_str`マクロを使用して優先的に構築されるべきです：`re"ab+c?"`。正規表現は、`*`、`|`、`&`、および`\`を使用して他の正規表現、文字列、または文字と組み合わせることができます：

  * `a * b` は、最初に `a` に一致し、その後 `b` に一致する入力に一致します
  * `a | b` は、`a` または `b` に一致する入力に一致します
  * `a & b` は、`a` と `b` の両方に一致する入力に一致します
  * `a \ b` は、`a` に一致するが `b` には一致しない入力に一致します
  * `!a` は、`a` に一致しないすべての入力に一致します。

正規表現にアクションを設定するには、[`onenter!`](@ref)、[`onexit!`](@ref)、[`onall!`](@ref)、および[`onfinal!`](@ref)を使用し、前提条件を設定するには[`precond!`](@ref)を使用します。

# 例

```julia
julia> regex = (re"a*b?" | opt('c')) * re"[a-z]+";

julia> regex = rep1((regex \ "aba") & !re"ca");

julia> regex isa RE
true

julia> compile(regex) isa Automa.Machine
true
```

参照： [`@re_str`](@ref)、[`compile`](@ref Main.Automa.compile)
