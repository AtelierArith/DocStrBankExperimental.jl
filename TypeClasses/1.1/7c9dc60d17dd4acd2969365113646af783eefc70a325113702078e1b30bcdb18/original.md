```
combine(::T, ::T)::T  # overload this
⊕(::T, ::T)::T  # alias \oplus
combine(a, b, c, d, ...)  # using combine(a, b) internally
```

Associcative combinator operator.

The symbol `⊕` (\oplus) following http://hackage.haskell.org/package/base-unicode-symbols-0.2.3/docs/Data-Monoid-Unicode.html

# Following Laws should hold

Associativity

```
⊕(::T, ⊕(::T, ::T)) == ⊕(⊕(::T, ::T), ::T)
```
