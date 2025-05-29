```
collect_columns(itr)
```

Collect an iterable as a `Columns` object if it iterates `Tuples` or `NamedTuples`, as a normal `Array` otherwise.

# Examples

```
s = [(1,2), (3,4)]
collect_columns(s)

s2 = Iterators.filter(isodd, 1:8)
collect_columns(s2)
```
