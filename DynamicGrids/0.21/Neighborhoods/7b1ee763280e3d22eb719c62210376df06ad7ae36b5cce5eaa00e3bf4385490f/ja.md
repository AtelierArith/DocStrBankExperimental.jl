```
Window <: Neighborhood

Window(; radius=1, ndims=2)
Window{R}(; ndims=2)
Window{R,N}()
```

中心セルを含む半径Rの近傍。

半径 `R = 1`:

```
N = 1   N = 2
        
 ▄▄▄     ███
         ▀▀▀
```

半径 `R = 2`:

```
N = 1   N = 2

        █████
▀▀▀▀▀   █████
        ▀▀▀▀▀
```
