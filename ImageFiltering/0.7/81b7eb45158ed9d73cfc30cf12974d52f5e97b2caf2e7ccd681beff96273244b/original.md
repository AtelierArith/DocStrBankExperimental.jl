```
imfilter([T], img, kernel, [border="replicate"], [alg]) --> imgfilt
imfilter([r], img, kernel, [border="replicate"], [alg]) --> imgfilt
imfilter(r, T, img, kernel, [border="replicate"], [alg]) --> imgfilt
```

Filter a one, two or multidimensional array `img` with a `kernel` by computing their correlation.

# Extended help

### Choices for `r`

Optionally, you can dispatch to different implementations by passing in a resource `r` as defined by the [ComputationalResources](https://github.com/timholy/ComputationalResources.jl) package.

For example:

```julia
imfilter(ArrayFireLibs(), img, kernel)
```

would request that the computation be performed on the GPU using the ArrayFire libraries.

### Choices for `T`

Optionally, you can control the element type of the output image by passing in a type `T` as the first argument.

### Choices for `img`

You can specify a one, two, or multidimensional array defining your image.

### Choices for `kernel`

The `kernel[0, 0,..]` parameter corresponds to the origin (zero displacement) of the kernel; you can use `centered` to place the origin at the array center, or use the OffsetArrays package to set `kernel`'s indices manually. For example, to filter with a random *centered* 3x3 kernel, you could use either of the following:

```julia
kernel = centered(rand(3,3))
kernel = OffsetArray(rand(3,3), -1:1, -1:1)
```

The `kernel` parameter can be specified as an array or as a "factored kernel", a tuple `(filt1, filt2, ...)` of filters to apply along each axis of the image. In cases where you know your kernel is separable, this format can speed processing. Each of these should have the same dimensionality as the image itself, and be shaped in a manner that indicates the filtering axis, e.g., a 3x1 filter for filtering the first dimension and a 1x3 filter for filtering the second dimension. In two dimensions, any kernel passed as a single matrix is checked for separability; if you want to eliminate that check, pass the kernel as a single-element tuple, `(kernel,)`.

### Choices for `border`

At the image edge, `border` is used to specify the padding which will be used to extrapolate the image beyond its original bounds.

#### `"replicate"` (default)

The border pixels extend beyond the image boundaries.

```plain
   ╭────┏━━━━━━┓────╮
   │aaaa┃abcdef┃ffff│
   ╰────┗━━━━━━┛────╯
```

#### `"circular"`

The border pixels wrap around. For instance, indexing beyond the left border returns values starting from the right border.

```plain

   ╭────┏━━━━━━┓────╮
   │cdef┃abcdef┃abcd│
   ╰────┗━━━━━━┛────╯

```

#### `"reflect"`

The border pixels reflect relative to a position between pixels. That is, the border pixel is omitted when mirroring.

```plain

   ╭────┏━━━━━━┓────╮
   │dcba┃abcdef┃fedc│
   ╰────┗━━━━━━┛────╯

```

#### `"symmetric"`

The border pixels reflect relative to the edge itself.

```plain

   ╭────┏━━━━━━┓────╮
   │edcb┃abcdef┃edcb│
   ╰────┗━━━━━━┛────╯

```

#### `Fill(m)`

The border pixels are filled with a specified value $m$.

```plain

   ╭────┏━━━━━━┓────╮
   │mmmm┃abcdef┃mmmm│
   ╰────┗━━━━━━┛────╯

```

#### `Inner()`

Indicate that edges are to be discarded in filtering, only the interior of the result is to be returned.

#### `NA()`

Choose filtering using "NA" (Not Available) boundary conditions. This is most appropriate for filters that have only positive weights, such as blurring filters.

See also: [`Pad`](@ref), [`padarray`](@ref), [`Inner`](@ref), [`NA`](@ref)  and [`NoPad`](@ref)

### Choices for `alg`

The `alg` parameter allows you to choose the particular algorithm: `Algorithm.FIR()` (finite impulse response, aka traditional digital filtering) or `Algorithm.FFT()` (Fourier-based filtering). If no choice is specified, one will be chosen based on the size of the image and kernel in a way that strives to deliver good performance. Alternatively you can use a custom filter type, like [`KernelFactors.IIRGaussian`](@ref).
