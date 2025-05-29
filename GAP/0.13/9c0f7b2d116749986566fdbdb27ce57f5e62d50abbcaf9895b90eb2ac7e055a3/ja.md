```
@gap <expr>
@gap(<expr>)
```

GAPで直接<expr>を実行します。これは、`GAP.evalstr("<expr>")`が呼び出されたかのように動作します。これは、Juliaから直接GAPリテラルを作成するために使用できます。

# 例

```jldoctest
julia> @gap [1,2,3]
GAP: [ 1, 2, 3 ]

julia> @gap SymmetricGroup(3)
GAP: Sym( [ 1 .. 3 ] )

julia> @gap(SymmetricGroup)(3)
GAP: Sym( [ 1 .. 3 ] )

```

最後の2つの例には、わずかな文法的、したがって意味的な違いがあります。最初のものは、GAP内で文字列`SymmetricGroup(3)`を直接実行します。2番目の例は、`@gap(SymmetricGroup)`を介して関数`SymmetricGroup`を返し、その後引数`3`でその関数を呼び出します。

Juliaのマクロのコードに引数を渡す方法のため、すべての有効なGAPコードを表す式を処理できるわけではありません。たとえば、複数のサイクルからなる置換のGAP構文や、非密なリストのGAP構文は問題を引き起こします。

```
julia> @gap (1,2,3)
GAP: (1,2,3)

julia> @gap (1,2)(3,4)
ERROR: LoadError: Error thrown by GAP: Error, no method found! For debugging hints type ?Recovery from NoMethodFound
[...]

julia> @gap [ 1,, 2 ]
ERROR: syntax: unexpected ","
[...]

```

文字列引数は`GAP.evalstr`で評価されることにも注意してください。

```jldoctest
julia> @gap "\"abc\""
GAP: "abc"

julia> @gap "[1,,2]"
GAP: [ 1,, 2 ]

julia> @gap "(1,2)(3,4)"
GAP: (1,2)(3,4)

```
