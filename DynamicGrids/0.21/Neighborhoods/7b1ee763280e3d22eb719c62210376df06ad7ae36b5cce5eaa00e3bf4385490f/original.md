```
Window <: Neighborhood

Window(; radius=1, ndims=2)
Window{R}(; ndims=2)
Window{R,N}()
```

A neighboorhood of radius R that includes the central cell.

Radius `R = 1`:

```
N = 1   N = 2
        
 ▄▄▄     ███
         ▀▀▀
```

Radius `R = 2`:

```
N = 1   N = 2

        █████
▀▀▀▀▀   █████
        ▀▀▀▀▀
```
