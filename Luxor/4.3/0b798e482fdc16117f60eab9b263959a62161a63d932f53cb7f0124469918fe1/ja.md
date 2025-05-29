```
polytopath(ptlist)
```

多角形をPathオブジェクトに変換します。

```julia
@draw drawpath(polytopath(ngon(O, 145, 5, vertices = true)), action = :fill)
```
