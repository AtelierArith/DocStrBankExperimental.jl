```
toexpr(ex, [st,])
```

シンボリック表現を `Expr` に変換し、`eval` に渡すのに適した形式にします。

例えば、

```julia
julia> @syms a b
(a, b)

julia> toexpr(a+b)
:((+)(a, b))

julia> toexpr(a+b) |> dump
Expr
  head: Symbol call
  args: Array{Any}((3,))
    1: + (function of type typeof(+))
    2: Symbol a
    3: Symbol b
```

関数は実際の関数オブジェクトであることに注意してください。

より複雑な表現については、他のコード関連のコンビネータを参照してください。

具体的には `Assignment`、`Let`、`Func`、`SetArray`、`MakeArray`、`MakeSparseArray` および `MakeTuple` です。

`toexpr` を使用して `Expr` に変換可能な独自の型を作成するには、`toexpr(x, st)` を定義し、内部呼び出しで状態 `st` を `toexpr` に渡します。`st` は、`y(t)` のようなものをそのままにするか、`var"y(t)"` にするかを知るために使用される状態です。例えば、`y(t)` が `y` ではなく関数の引数である場合です。
