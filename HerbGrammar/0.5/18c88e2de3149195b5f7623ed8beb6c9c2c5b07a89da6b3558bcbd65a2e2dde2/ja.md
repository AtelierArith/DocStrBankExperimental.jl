```
@csgrammar
```

[`ContextSensitiveGrammar`](@ref) を定義するためのマクロです。AbstractConstraints は、[`addconstraint!`](@ref) 関数を使用して後から追加できます。

### 使用例:

```julia
grammar = @csgrammar begin
	R = x
	R = 1 | 2
	R = R + R
end
```

### 構文:

  * リテラル: Julia で既に定義されているシンボルはリテラルと見なされます。例えば `1`、`2`、または `π` です。例: `R = 1`。
  * 変数: 変数は非終端シンボルではなく、Julia で既に定義されていないシンボルです。例: `R = x`。
  * 関数: Julia または `Main` モジュールで定義された関数や中置演算子は、デフォルトの評価器で使用できます。例: `R = R + R`、`R = f(a, b)`。
  * 組み合わせ: 複数のルールは、`|` シンボルを使用して文法定義の単一行で定義できます。例: `R = 1 | 2 | 3`。
  * イテレータ: 複数のルールを定義する別の方法は、`|` シンボルの後に Julia イテレータを提供することです。例: `R = |(1:9)`。

### 関連:

  * [`@pcsgrammar`](@ref) は、確率的 [`ContextSensitiveGrammar`](@ref) を作成するために似た構文を使用します。
