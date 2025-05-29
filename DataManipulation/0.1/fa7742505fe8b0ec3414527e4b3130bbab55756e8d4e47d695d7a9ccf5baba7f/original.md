```
ss"substitution"
```

"Static" substitution string in the type domain. The underlying value can be extracted with the `unstatic()` function.

See also: `sr"regex"`, `nest`.

# Examples

```julia
nt = (a_1=1, a_2=10, b_1=100)

# select and rename by regex and substitution string:
nt[sr"a_(\d)" => ss"xxx_\1_xxx"] === (xxx_1_xxx = 1, xxx_2_xxx = 10)
```
