```
rm_lineinfo(ex)
```

Remove `LineNumberNode` in a given expression.

!!! tips
    the `LineNumberNode` inside macro calls won't be removed since the `macrocall` expression requires a `LineNumberNode`. See also [issues/#9](https://github.com/Roger-luo/Expronicon.jl/issues/9).

