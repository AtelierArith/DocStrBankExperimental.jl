```
(choices1, choices2) = unpair(choices::ChoiceMap, key1::Symbol, key2::Symbol)
```

Return the two sub-assignments at `key1` and `key2`, one or both of which may be empty.

It is an error if there are any top-level values, or any non-empty top-level sub-assignments at keys other than `key1` and `key2`.
