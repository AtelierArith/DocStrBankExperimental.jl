```
isrepresented(object::MLJType, objects)
```

Test if `object` has a representative in the iterable `objects`. This is a weaker requirement than `object in objects`.

Here we say `m1` *represents* `m2` if `is_same_except(m1, m2)` is `true`.
