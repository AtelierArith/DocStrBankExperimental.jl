```julia
sync_bounds(tag, collection)

```

Make sure that axis bounds are the same for axes as determined by `tag` (see below).

Tag can be given in the form of `Val(tag)` too, this is a convenience wrapper.

Possible tags:

  * `:X`, `:Y`, `:XY`: make the specified axes in *all* items of the collection the same
  * `:x`, `:y`, `:xy`: make x/y axes the same in plots that are in the same column/row, only works for

`:x`, `:y`, and `:xy` only work for matrix-like arguments.

All methods return the (modified) first argument.

# Explanation

To illustrate the lowercase tags, consider the arrangement

```ascii
y/vertical axis
│
│ C  D
│ A  B
└────────x/horizontal axis
```

which could be entered as eg

```julia
t = Tableau([A C; B D])
```

Then `sync_bounds(:x, t)` would ensure that A and C have the same bounds for the x-axis, and similarly B and D.
