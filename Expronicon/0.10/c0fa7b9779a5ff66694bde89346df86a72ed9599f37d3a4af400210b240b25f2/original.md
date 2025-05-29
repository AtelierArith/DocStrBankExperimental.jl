```
prettify(ex; kw...)
```

Prettify given expression, remove all `LineNumberNode` and extra code blocks.

# Options (Kwargs)

All the options are `true` by default.

  * `rm_lineinfo`: remove `LineNumberNode`.
  * `flatten_blocks`: flatten `begin ... end` code blocks.
  * `rm_nothing`: remove `nothing` in the `begin ... end`.
  * `preserve_last_nothing`: preserve the last `nothing` in the `begin ... end`.
  * `rm_single_block`: remove single `begin ... end`.
  * `alias_gensym`: replace `##<name>#<num>` with `<name>_<id>`.
  * `renumber_gensym`: renumber the gensym id.

!!! tips
    the `LineNumberNode` inside macro calls won't be removed since the `macrocall` expression requires a `LineNumberNode`. See also [issues/#9](https://github.com/Roger-luo/Expronicon.jl/issues/9).

