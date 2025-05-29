```
trace(f, args...; is_primitive, primitives)
```

Trace function call, produce call value and a Tape.

`trace` records to the tape primitive methods and recursively dives into non-primitives. There are 2 ways to tell `trace` that a particular method is a primitive:

  * provide `is_primitive(sig) -> Bool` function, where `sig` is   is a method signature, e.g. `Tuple{map(typeof, (f, args...))...}`
  * provide an iterable `primitives`; in this case `trace` matches   all methods of this function
