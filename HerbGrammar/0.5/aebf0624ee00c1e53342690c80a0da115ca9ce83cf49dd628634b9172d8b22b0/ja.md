```
@pcsgrammar
```

確率的 [`ContextSensitiveGrammar`](@ref) を定義するためのマクロです。

### 使用例:

```julia
grammar = @pcsgrammar begin
	0.5 : R = x
	0.3 : R = 1 | 2
	0.2 : R = R + R
end
```

### 構文:

ルールの構文は [`@csgrammar`](@ref) で使用される構文と同じです:

  * リテラル: Julia で既に定義されているシンボルはリテラルと見なされます。例えば `1`、`2`、または `π` などです。例: `R = 1`。
  * 変数: 変数は非終端シンボルではなく、Julia で既に定義されていないシンボルです。例: `R = x`。
  * 関数: Julia または `Main` モジュールで定義された関数や中置演算子は、デフォルトの評価器で使用できます。例: `R = R + R`、`R = f(a, b)`。
  * 組み合わせ: 複数のルールは、`|` シンボルを使用して文法定義の単一行で定義できます。例: `R = 1 | 2 | 3`。
  * イテレータ: 複数のルールを定義する別の方法は、`|` シンボルの後に Julia のイテレータを提供することです。例: `R = |(1:9)`。

すべてのルールには確率が接頭辞として付けられています。ルールと確率は `:` シンボルで区切られます。単一行で複数のルールが定義されている場合、確率はルール間で均等に分配されます。特定の非終端シンボルのすべてのルールの確率の合計は 1 に等しくなければなりません。この場合、確率は自動的にスケーリングされます。

### 関連:

  * [`@csgrammar`](@ref) は、非確率的な [`ContextSensitiveGrammar`](@ref) を作成するために似た構文を使用します。
