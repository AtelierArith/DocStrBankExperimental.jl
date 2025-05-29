```
evaluate(p::Predicate, args...)
```

Evaluate a predicate for given arguments.

### Input

  * `p`    – predicate
  * `args` – argument list

### Output

A `Bool` corresponding to the evaluation of `p(args)`.

### Notes

We offer `p(args)` as a short-hand version of `evaluate(p, args)`.
