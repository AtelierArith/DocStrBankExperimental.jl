```julia
lexer(name)

```

指定された名前 `name` に関連付けられた `AbstractLexer` を返します。`name` は文字列でなければなりません。内部的には、各レキサ定義の `:aliases` フィールドをチェックして、一致するかどうかを確認します。

!!! warning
    このメソッドは *型安定* ではありません。


指定された `name` に一致するレキサがない場合、`ArgumentError` がスローされます。
