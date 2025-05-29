```
liftM(f::Callable, M::MonadClass, args...)
(M::MonadClass).liftM(f, args...)
```

関数 `f` をモナディックコンテキストに持ち上げます。

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> liftM(-, Maybe, Some(1)) === Maybe.liftM(-, Some(1)) === Some(-1)
true

julia> Maybe.liftM(+, Some(1), Some(2), Some(3))
Some(6)
```

---

```
liftM(op, M::MonadClass)
(M::MonadClass).liftM(op)
```

演算子 `op` をモナディックコンテキストに持ち上げたものを返します。

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> let ⊕ = Maybe.liftM(+)
           Some(1) ⊕ Some(2) ⊕ Some(3)
       end
Some(6)
```
