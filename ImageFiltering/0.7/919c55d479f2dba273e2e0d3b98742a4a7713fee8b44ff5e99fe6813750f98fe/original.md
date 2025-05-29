```
padarray([T], img, border)
```

Generate a padded image from an array `img` and a specification `border` of the boundary conditions and amount of padding to add.

Return a padded image. The function supports one, two or multi-dimensional images. You can specify the element type `T` of the output image.

See [`Pad`](@ref) and [`Fill`](@ref) for details.

# Examples

## Padding

The main syntax for `Pad` is `(style, m, n, ...)` or `(style, (m, n))`, where `m` pixels are added to dimension 1 (top and bottom), `n` pixels for dimension 2, and so forth.

Add 30 to left and right, 40 to top and bottom:

```julia
padarray(A, Pad(:replicate, 30, 40))
padarray(A, Pad(:circular, 30, 40))
padarray(A, Pad(:symmetric, 30, 40))
padarray(A, Pad(:reflect, 30, 40))
```

Add 30 above, 40 to left, 50 to bottom, 60 to right:

```julia
padarray(A, Pad(0, (30, 40), (50, 60)))
padarray(A, Pad(0, (30, 40), (50, 60)))
```

# 3D

```julia
padarray(A, Pad(:replicate, 1, 1, 1)) 
padarray(A, Fill(0, (1, 1, 1))) 
```

## Filling

The main syntax for `Fill` is `(value, m, n)` or `(value, (m, n))` where the image is prepended by `m` pixels and appended by `n` pixels in each dimension.

Add 20 `-1` values above, 30 to left, 40 to bottom, 50 to right:

```julia
padarray(A, Fill(-1, (20, 30), (40, 50))) 
```
