```
neutral
neutral(::Type)
neutral(_default_return_value) = neutral
```

Neutral element for `⊕`, also called "identity element". `neutral` is a function which can give you  the neutral element for a concrete type, or alternatively you can use it as a singleton value which combines with everything.

By default `neutral(type)` will return the generic `neutral` singleton. You can override it for your specific type to have a more specific neutral value.

We decided for name `neutral` according to https://en.wikipedia.org/wiki/Identity_element. Alternatives seem inappropriate

  * "identity" is already taken
  * "identity_element" seems to long
  * "I" is too ambiguous
  * "unit" seems ambiguous with physical units

## Following Laws should hold

Left Identity

```
  ⊕(neutral(T), t::T) == t
```

Right Identity

```
  ⊕(t::T, neutral(T)) == t
```
