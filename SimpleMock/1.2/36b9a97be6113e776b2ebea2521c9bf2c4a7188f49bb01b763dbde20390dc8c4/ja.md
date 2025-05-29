```
mock(f::Function[, ctx::Symbol], args...; filters::Vector{<:Function}=Function[])
```

指定された関数をモックアウトして `f` を実行します。

!!! note
    キーワード引数を持つ関数のモッキングは部分的にのみサポートされています。詳細については、以下の「キーワード引数」セクションを参照してください。


## 例

単一の関数をモックする:

```julia
f(x) = x + 1
mock(+) do plus
    @assert plus isa Mock
    @assert f(0) != 1  # + への呼び出しはモックされています。
    @assert called_once_with(plus, 0, 1)
end
```

カスタム [`Mock`](@ref) を使用して関数をモックする:

```julia
mock((+) => Mock(1)) do plus
    @assert 1 + 1 == 1
    @assert called_once_with(plus, 1, 1)
end
```

指定されたシグネチャに一致するメソッドをモックする:

```julia
mock((+, Float64, Float64) => Mock((a, b) -> 2a + 2b)) do plus
    @assert 1 + 1 == 2
    @assert 2.0 + 2.0 == 8
    @assert called_once_with(plus, 2.0, 2.0)
end
```

`Mock` 以外のものでモックする:

```julia
mock((+) => (a, b) -> 2a + 2b) do _plus
    @assert 1 + 2 == 6
end
```

## フィルターの使用

多くの場合、モックを行う関数には、どこでそのモッキングを行いたいかについて非常に具体的なアイデアがあります。予期しない呼び出しがコールスタックの深いところでモックされると混乱することがあります。これを避けるために、次のようにフィルタ関数を使用できます:

```julia
f(x, y) = x + y
g(x, y) = f(x, y)
mock((+) => Mock((a, b) -> 2a + 2b); filters=[max_depth(2)]) do plus
    @assert f(1, 2) == 6  # ここでの + の呼び出し深度は 2 です。
    @assert g(3, 4) == 7  # ここでは 3 です。
    @assert called_once_with(plus, 1, 2)
end
```

フィルタ関数は、[`Metadata`](@ref) 型の単一の引数を取ります。いずれかのフィルタが拒否した場合、モッキングは行われません。含まれているフィルタのリストや、自分自身のフィルタを作成するためのビルディングブロックについては、[フィルタ関数](@ref)を参照してください。

## `Context` の再利用

内部的に、この関数はデフォルトで毎回新しい [Cassette `Context`](https://jrevels.github.io/Cassette.jl/stable/api.html#Cassette.Context) を作成します。これにより、クリーンなモッキング環境が提供されますが、新しい型やメソッドを何度も作成して呼び出すのは遅くなることがあります。同じ関数のセットを繰り返しモックする場合は、次のようにコンテキスト名を指定してそのコンテキストを再利用できます:

```julia
ctx = gensym()
mock(g -> @assert(!called(g)), ctx, get)
# これの方が速いです、特にモックブロック内で多くのことが行われている場合。
mock(g -> @assert(!called(g)), ctx, get)
```

## キーワード引数

キーワード引数を持つ関数のモッキングは、以下の条件が満たされている場合に完全にサポートされています:

  * フィルタ関数が使用されていない
  * 使用中のコンテキストに、現在モック解除された関数がない

フィルタ関数が拒否し、モックされた関数（そのモックではなく）を呼び出すと、その呼び出しにはキーワードがありません。

以前にモックされた関数を持つコンテキストを再利用すると、その関数へのモック解除された呼び出しにはキーワードがありません。例えば:

```julia
kwfunc(; kwargs...) = nothing
calls_kwfunc(; kwargs...) = kwfunc(; kwargs...)
ctx = gensym()
mock(ctx, calls_kwfunc) do c
    calls_kwfunc(; x=1, y=2)
    @assert called_once_with(c; x=1, y=2)
end
mock(ctx, kwfunc) do k
    calls_kwfunc(; x=1, y=2)               # これは警告を発します。
    @assert called_once_with(k; x=1, y=2)  # これは失敗します！
end
```

要するに、キーワードを受け入れる関数をモックする際には、フィルタやコンテキストの再利用を避けてください。
