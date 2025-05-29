```
grid!(content::Vararg{Pair}; kwargs...)
```

Creates a GridLayout with all pairs contained in `content`. Each pair consists of an iterable with row and column spans, and a content object. Each content object is then placed in the GridLayout at the span from its pair.

Example:

grid!(     [1, 1] => obj1,     [1, 2] => obj2,     [2, :] => obj3, )
