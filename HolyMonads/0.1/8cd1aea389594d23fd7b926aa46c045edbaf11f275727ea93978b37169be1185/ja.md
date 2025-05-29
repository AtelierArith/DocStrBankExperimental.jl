```
@do モナドブロック
Monad.@do ブロック
```

モナドのための do 表記。別名計算式。

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> result = Maybe.@do begin
           a ← Some(1)
           b ← Some(2)
           return a + b
       end
Some(3)
```
