```
sr"regex"
```

"Static" regular expression in the type domain. The most direct use is indexing `NamedTuple`s and selecting columns from type-stable tables such as `StructArray`s. The underlying value can be extracted with the `unstatic()` function.

See also: `ss"substitution"`, `nest`.

# Examples

```julia
nt = (a_1=1, a_2=10, b_1=100)

# select a subset of nt by regex:
nt[sr"a_\d"] === (a_1 = 1, a_2 = 10)

# select and rename by regex and substitution string:
nt[sr"a_(\d)" => ss"xxx_\1_xxx"] === (xxx_1_xxx = 1, xxx_2_xxx = 10)
```
