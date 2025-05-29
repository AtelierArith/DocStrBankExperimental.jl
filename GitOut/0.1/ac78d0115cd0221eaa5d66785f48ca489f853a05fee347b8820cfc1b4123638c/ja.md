```julia
git(args; post_args, kw...) -> Cmd

```

`git()`](@ref)と同様に、追加の引数を持つ`git` `Cmd`オブジェクトを作成します。`post_args`引数からの引数は、常に`arg`からの引数の後に適用されます。これは、`args`に直接アクセスを提供しない他の関数にとって便利です。たとえば、`push(r; post_args=(tags=true,))`は`push(r, tags=true)`と同等です。

引数は配列またはキーと値のコレクションとして渡すことができ、キーは引数フラグ名です。
