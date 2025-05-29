```
@expect(defn)
```

Prepares a stub, lets it know to expect a function call matching the `defn`, and to return the result.

Has several forms, which align to julia function declations. Examples:

  * `@expect(foo(1, 1.5)=10)` this prepares the stub `foo`, to return 10, if it gets given the input `(1, 1.5)`
  * `@expect(foo(3, ::Int)=20)` this prepares the stub `foo`, to return 20, if it gets given the input with first arguement 3, and second argument any `Int`
  * `@expect(foo(5, ::Any)=30)` this prepares the stub `foo`, to return 30, if it gets given the input with first arguement 5, and second argument any type
  * `@expect(foo(Any, ::Any)=40)` this prepares the stub `foo`, to return 40, if it is given 2 arguements

Notes that you can not for the same stub both the declare that it is bound by type (i.e. that it can take anything of a given type), and declare that it is bound by value, for the same parameter.

Note that the result can not depend on the arguments of the function. This is intentional, as it is there to keep your Stubs simple and to the point. So you don't end up needing to test your tests.

Currently does not support KWArgs.
