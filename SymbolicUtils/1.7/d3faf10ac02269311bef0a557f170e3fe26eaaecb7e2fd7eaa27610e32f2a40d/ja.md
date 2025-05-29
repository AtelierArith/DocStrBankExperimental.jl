similarterm(x, head, args, symtype=nothing; metadata=nothing, exprhead=:call)

`typeof(x)`と同じ型のクロージャにある項を返します。`head`は先頭、`args`は引数、`type`はsymtype、`metadata`はメタデータとして使用されます。デフォルトでは`head(args...)`が実行されます。`x`パラメータは`Type`でも構いません。`exprhead`キーワード引数は`Expr`を操作する際に便利です。
