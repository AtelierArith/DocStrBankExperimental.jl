```
fmap(f::Callable, M::MonadClass, t)
(M::MonadClass).fmap(f, t)
```

`f`をモナディックコンテキスト`t`内の値に適用した結果のモナディックコンテキストを返します。Juliaの`do`構文を使用して、関数`f`をブロックとして渡すことができます。(fmap :: MonadClass M: (x -> y) -> M x -> M y) (いわゆる`flatmap`)

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> fmap(Maybe, Some(1)) do x
           x + 1
       end === Maybe.fmap(x -> x + 1, Some(1)) === Some(2)
true
```
