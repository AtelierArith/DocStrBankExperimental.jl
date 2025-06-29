```
Moore <: Neighborhood

Moore(radius::Int=1; ndims=2)
Moore(; radius=1, ndims=2)
Moore{R}(; ndims=2)
Moore{R,N}()
```

Moore neighborhoods define the neighborhood as all cells within a horizontal or vertical distance of the central cell. The central cell is omitted.

Radius `R = 1`:

```
N = 1   N = 2
 
 ▄ ▄     █▀█
         ▀▀▀
```

Radius `R = 2`:

```
N = 1   N = 2

        █████
▀▀ ▀▀   ██▄██
        ▀▀▀▀▀
```

Using `R` and `N` type parameters removes runtime cost of generating the neighborhood, compated to passing arguments/keywords.
