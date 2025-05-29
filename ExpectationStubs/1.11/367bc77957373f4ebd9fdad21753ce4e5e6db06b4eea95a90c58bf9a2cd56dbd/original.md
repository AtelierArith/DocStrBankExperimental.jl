```
@used(defn)
```

Returns true if a particular expectionation was used. Syntax is similar to `@expect`

Like `@expect` the key can be a value or a type. It does not have to match to the one that was used in `@expect`

Normally one would used this inside a test:

  * `@test @used(foo(1, 1.5))` test that `foo` was called with `(1, 1.5)`
  * `@test @used(foo(3, ::Int))` test the `foo` was called with 3 and some Int
  * `@test !@used(foo(5, ::Any))` test that `foo` was never called with the first arg 5 (and exactly 2 args)
  * `@test !@used(foo(Any, ::Any))` test tjat `foo` was never alled with 2 args
