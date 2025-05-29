```
PyIO(f, x; ...)
```

Equivalent to `f(PyIO(x; ...))` except the stream is automatically flushed or closed according to `own`.

For use in a `do` block, as in

```
PyIO(x, ...) do io
    ...
end
```
