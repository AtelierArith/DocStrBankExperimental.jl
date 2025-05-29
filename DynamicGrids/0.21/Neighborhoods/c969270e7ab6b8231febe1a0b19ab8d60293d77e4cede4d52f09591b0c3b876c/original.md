```
VonNeumann(radius=1; ndims=2) -> Positional
VonNeumann(; radius=1, ndims=2) -> Positional
VonNeumann{R,N}() -> Positional
```

A Von Neuman neighborhood is a damond-shaped, omitting the central cell:

Radius `R = 1`:

```
N = 1   N = 2

 ▄ ▄     ▄▀▄
          ▀
```

Radius `R = 2`:

```
N = 1   N = 2

         ▄█▄
▀▀ ▀▀   ▀█▄█▀
          ▀
```

In 1 dimension it is identical to [`Moore`](@ref).

Using `R` and `N` type parameters removes runtime cost of generating the neighborhood, compated to passing arguments/keywords.
