```
Differential(x)
```

Use to find (partial) derivatives.

## Example

```
@syms x y u()
Dx = Differential(x)
Dx(u(x,y))  # resolves to diff(u(x,y),x)
Dx(u)       # will evaluate diff(u(x), x)
(Dx^2)(u(x))  # two derivatives in x; not () to avoid 2u(x) eager evaluation
```
