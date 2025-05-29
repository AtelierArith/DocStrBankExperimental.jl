```
mbind(f::Callable, M::MonadClass, t)
(M::MT).mbind(f, t)
```

`f`をモナディックコンテキスト`t`の値に適用した結果のモナディックコンテキストを返します。Juliaの`do`構文を使用して、関数`f`をブロックとして渡すことができます。(mbind :: MonadClass M: (x -> M y) -> M x -> M y) (いわゆる`bind`)

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> mbind(Maybe, Some(1)) do x
           unit(Maybe, x + 1)
       end === Maybe.mbind(x -> Maybe.unit(x + 1), Some(1)) === Some(2)
true
```
