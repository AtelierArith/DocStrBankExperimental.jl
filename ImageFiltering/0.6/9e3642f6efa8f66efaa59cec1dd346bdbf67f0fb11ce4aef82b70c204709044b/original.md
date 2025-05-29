```julia
    struct Pad{N} <: AbstractBorder
        style::Symbol
        lo::Dims{N}    # number to extend by on the lower edge for each dimension
        hi::Dims{N}    # number to extend by on the upper edge for each dimension
    end
```

`Pad` is a type that designates the form of padding which should be used to extrapolate pixels beyond the boundary of an image. Instances must set `style`, a Symbol specifying the boundary conditions of the image.

# Output

The type `Pad` specifying how the boundary of an image should be padded.

# Details

When representing a spatial two-dimensional image filtering operation as a discrete convolution between the image and a $D \times D$ filter, the results are undefined for pixels closer than $D$ pixels from the border of the image. To define the operation near and at the border, one needs a scheme for extrapolating pixels beyond the edge. The `Pad` type allows one to specify the necessary extrapolation scheme.

The type facilitates the padding of one, two or multi-dimensional images.

You can specify a different amount of padding at the lower and upper borders of each dimension of the image (top, left, bottom and right in two dimensions).

## Options

Some valid `style` options are described below. As an indicative example of each option the results of the padding are illustrated on an image consisting of a row of six pixels which are specified alphabetically: $\boxed{a \, b \, c \,d \, e \, f}$. We show the effects of padding only on the left and right border, but analogous consequences hold for the top and bottom border.

### `:replicate` (Default)

The border pixels extend beyond the image boundaries.

$$
\boxed{
\begin{array}{l|c|r}
  a\, a\, a\, a  &  a \, b \, c \, d \, e \, f & f \, f \, f \, f
\end{array}
}
$$

See also: [`Fill`](@ref), [`padarray`](@ref), [`Inner`](@ref) and [`NoPad`](@ref)

### `:circular`

The border pixels wrap around. For instance, indexing beyond the left border returns values starting from the right border.

$$
\boxed{
\begin{array}{l|c|r}
  c\, d\, e\, f  &  a \, b \, c \, d \, e \, f & a \, b \, c \, d
\end{array}
}
$$

See also: [`Fill`](@ref), [`padarray`](@ref), [`Inner`](@ref) and [`NoPad`](@ref)

### `:symmetric`

The border pixels reflect relative to a position between pixels. That is, the border pixel is omitted when mirroring.

$$
\boxed{
\begin{array}{l|c|r}
  e\, d\, c\, b  &  a \, b \, c \, d \, e \, f & e \, d \, c \, b
\end{array}
}
$$

See also: [`Fill`](@ref),[`padarray`](@ref), [`Inner`](@ref) and [`NoPad`](@ref)

### `:reflect`

The border pixels reflect relative to the edge itself.

$$
\boxed{
\begin{array}{l|c|r}
  d\, c\, b\, a  &  a \, b \, c \, d \, e \, f & f \, e \, d \, c
\end{array}
}
$$

See also: [`Fill`](@ref),[`padarray`](@ref), [`Inner`](@ref) and [`NoPad`](@ref)

---
