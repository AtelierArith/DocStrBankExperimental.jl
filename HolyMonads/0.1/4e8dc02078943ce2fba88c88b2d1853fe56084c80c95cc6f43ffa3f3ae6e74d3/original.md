```
liftM(f::Callable, M::MonadClass, args...)
(M::MonadClass).liftM(f, args...)
```

Lifts a function `f` to a monadic context.

# Example

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

Returns a lifted operator of `op` to a monadic context.

# Example

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> let ⊕ = Maybe.liftM(+)
           Some(1) ⊕ Some(2) ⊕ Some(3)
       end
Some(6)
```
