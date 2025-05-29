```
expr2pcsgrammar(ex::Expr)::ContextSensitiveGrammar
```

`Expr`を確率を持つ[`ContextSensitiveGrammar`](@ref)に変換するための関数です。式がハードコーディングされている場合は、`@pcsgrammar`マクロを使用する必要があります。正しい形式の式のみが変換可能です（[`@pcsgrammar`](@ref)を参照）。

### 使用例:

```@example
grammar = expr2pcsgrammar(
	begin
		0.5 : R = x
		0.3 : R = 1 | 2
		0.2 : R = R + R
	end
)
```
