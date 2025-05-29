```
a ↠ b = flatmap(_ -> b, a) # \twoheadrightarrow
```

A convenience operator for monads which just applies the second monad within the first one.

The operator ↠ (\twoheadrightarrow) is choosen because the other favourite ≫ (\gg) which would have been in accordance  with [haskell unicode syntax for monads](https://hackage.haskell.org/package/base-unicode-symbols-0.2.4.2/docs/Control-Monad-Unicode.html) is unfortunately parsed as boolean comparison with extra semantics which leads to errors with non-boolean applications.

↠ is just the most similar looking other operator which does not have this restriction and is right-associative.
