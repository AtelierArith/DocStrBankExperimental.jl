```julia
    struct Fill{T,N} <: AbstractBorder
        value::T
        lo::Dims{N}
        hi::Dims{N}
    end
```

`Fill` is a type that designates a particular value which will be used to extrapolate pixels beyond the boundary of an image.

# Output

The type `Fill` specifying the value with which the boundary of the image should be padded.

# Details

When representing a two-dimensional spatial image filtering operation as a discrete convolution between an image and a $D \times D$ filter, the results are undefined for pixels closer than $D$ pixels from the border of the image. To define the operation near and at the border, one needs a scheme for extrapolating pixels beyond the edge. The `Fill` type allows one to specify a particular value which will be used in the extrapolation. For more elaborate extrapolation schemes refer to the documentation of  [`Pad`](@ref).

The type facilitates the padding of one, two or multi-dimensional images.

You can specify a different amount of padding at the lower and upper borders of each dimension of the image (top, left, bottom and right in two dimensions).

# Example

As an indicative illustration consider an image consisting of a row of six pixels which are specified alphabetically: $\boxed{a \, b \, c \, d \, e \, f}$. We show the effects of padding with a constant value $m$ only on the left and right border, but analogous consequences hold for the top and bottom border.

$$
\boxed{
\begin{array}{l|c|r}
  m\, m\, m\, m  &  a \, b \, c \, d \, e \, f & m \, m \, m \, m
\end{array}
}
$$

See also: [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref) and [`NoPad`](@ref)

---
