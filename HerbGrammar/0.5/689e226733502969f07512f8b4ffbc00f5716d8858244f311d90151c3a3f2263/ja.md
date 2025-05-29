```
expr2csgrammar(ex::Expr)::ContextSensitiveGrammar
```

`Expr`を[`ContextSensitiveGrammar`](@ref)に変換するための関数です。式がハードコーディングされている場合は、[`@csgrammar`](@ref)マクロを使用する必要があります。正しい形式の式のみ（[`@csgrammar`](@ref)を参照）を変換できます。

### 使用例:

```@example
grammar = expr2csgrammar(
	begin
		R = x
		R = 1 | 2
		R = R + R
	end
)
```
