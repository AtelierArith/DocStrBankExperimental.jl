```
@syms <lhs_expr>[::T1] <lhs_expr>[::T2]...
```

例えば:

```
@syms foo::Real bar baz(x, y::Real)::Complex
```

1つ以上の変数を作成します。`<lhs_expr>`は単なるシンボルである場合、変数の名前になります。また、関数呼び出しである場合、呼び出される関数と同じ名前を持つ関数のような変数になります。Sym型、または関数のようなSymの場合、関数を呼び出す際の出力型は`::T`構文を使用して設定できます。

# 例:

  * `@syms foo bar::Real baz::Int`は次のように作成します

変数`foo`はsymtype `Number`（デフォルト）、`bar`はsymtype `Real`、`baz`はsymtype `Int`です。

  * `@syms f(x) g(y::Real, x)::Int h(a::Int, f(b))`は1引数の`f`、2引数の`g`

および2引数の`h`を作成します。`h`への2番目の引数は1引数の関数のような変数でなければなりません。したがって、`h(1, g)`は失敗し、`h(1, f)`は成功します。
