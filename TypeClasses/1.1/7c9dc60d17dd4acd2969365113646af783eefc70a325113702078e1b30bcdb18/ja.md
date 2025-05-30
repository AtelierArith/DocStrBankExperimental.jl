```
combine(::T, ::T)::T  # overload this
⊕(::T, ::T)::T  # alias \oplus
combine(a, b, c, d, ...)  # using combine(a, b) internally
```

結合的なコンビネータ演算子。

記号 `⊕` (\oplus) は http://hackage.haskell.org/package/base-unicode-symbols-0.2.3/docs/Data-Monoid-Unicode.html に従います。

# 次の法則が成り立つべきです

結合性

```
⊕(::T, ⊕(::T, ::T)) == ⊕(⊕(::T, ::T), ::T)
```
