```
draw(b::Backend, c::Context)
```

Output the tree-structured graphic in `c` to the given backend.

# Examples

```
draw(SVGJS("foo.svg"), compose(context(), text(0,0,"foo")))
```
