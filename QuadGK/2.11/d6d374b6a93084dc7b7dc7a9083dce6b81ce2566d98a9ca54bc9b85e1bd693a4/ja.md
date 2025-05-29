```
BatchIntegrand(f!, y::AbstractVector, [x::AbstractVector]; max_batch=typemax(Int))
BatchIntegrand{Y,X}(f!; max_batch=typemax(Int)) where {Y,X}
BatchIntegrand{Y}(f!; max_batch=typemax(Int)) where {Y}
```

`BatchIntegrand`のコンストラクタは、`f!(y,x) = y .= f.(x)`の形式の被積分関数を受け入れ、スレッド、GPU、または分散メモリを使用して複数の数値積分ノードで被積分関数を評価できます。引数`y`とオプションの`x`は、`f!`の定義域と値域に対して正しい要素型の事前に割り当てられたバッファです。さらに、評価ポイントの数は`f!`への呼び出し間で変わる可能性があるため、`resize!`可能でなければなりません。あるいは、これらのバッファの要素型`Y`とオプションの`X`をコンストラクタに型パラメータとして渡すこともできます。`max_batch`キーワードは、被積分関数に渡されるノードの数を大まかに制限しますが、少なくとも`4*order+2`のノードがGKルールによって使用されます。

## 内部割り当て

`x`または`X`が指定されていない場合、`quadgk`は内部的にユーザーが提供した`y`バッファと、ドメイン型に基づいて新たに割り当てられた`x`バッファを持つ新しい`BatchIntegrand`を作成します。したがって、呼び出し間で`x`バッファを再利用したい場合は、`{Y,X}`を指定するか、`y,x`を明示的に渡してください。
