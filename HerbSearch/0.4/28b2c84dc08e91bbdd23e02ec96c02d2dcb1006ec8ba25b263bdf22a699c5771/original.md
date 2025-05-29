```
@programiterator
```

Canonical way of creating a program iterator. The macro automatically declares the expected fields listed in the `ProgramIterator` documentation. Syntax accepted by the macro is as follows (anything enclosed in square brackets is optional):     `@programiterator [mutable] <IteratorName>(         <arg₁>,         ...,         <argₙ>     ) [<: <SupertypeIterator>]` Note that the macro emits an assertion that the `SupertypeIterator`  is a subtype of `ProgramIterator` which otherwise throws an ArgumentError. If no supertype is given, the new iterator extends `ProgramIterator` directly. Each <argᵢ> may be (almost) any expression valid in a struct declaration, and they must be comma separated. One known exception is that an inner constructor must always be given using the extended `function <name>(...) ... end` syntax. The `mutable` keyword determines whether the declared struct is mutable.
