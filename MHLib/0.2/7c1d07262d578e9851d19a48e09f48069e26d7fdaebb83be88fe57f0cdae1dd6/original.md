```
flip_variable!(::BoolVectorSolution, pos::Int)
```

Flip the value at the given position and return new objective value.

Should be overloaded with a problem-specific implementation realizing incremental evaluation if possible.
