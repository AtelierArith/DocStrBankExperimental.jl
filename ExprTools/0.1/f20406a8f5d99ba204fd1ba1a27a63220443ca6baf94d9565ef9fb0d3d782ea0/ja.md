```
args_tuple_expr(signature_def::Dict{Symbol})
args_tuple_expr(arg_exprs)
```

`arg_exprs`が`[:(x::Int), :(y::Float64), :(z::Vararg)]`のようなシグネチャからの位置引数式のリストである場合、またはその形式の`signature_def[:args]`値を含む全体の`signature_def` `Dict`である場合。

これは、名前で全ての引数を含むタプル式を返します。`Vararg`型のものに対するスプラッティングを正しく処理します。例えば、前の例では`:((x, y, z...))`のようになります。

これは、`signature_def[:body]`を修正するのに便利です。例えば、次のようにして全ての引数を出力することができます。

```julia
signature_def[:body] = quote
    args = $(args_tuple_expr(signature_def))
    println("args = ",args)
    $(signature_def[:body]) # 古いボディを挿入
end
```

より現実的な使用例は、元の関数と同じ引数を受け取る別の関数への呼び出しを挿入したい場合です。
