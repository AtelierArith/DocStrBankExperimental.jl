```
stem(x, y, onlyimpulses=false, [,axes] [, curve], args...) -> Gaston.Figure
```

Create a stem plot using `x` and `y`. If `onlyimpulses` is true, then the conventional circles indicating each sample are not drawn.

```
stem(x, f::Function, onlyimpulses=false, [,axes] [, curve], args...) -> Gaston.Figure
```

Use `y = f.(x)`
