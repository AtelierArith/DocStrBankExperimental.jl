```
Upsample(mode = :nearest; [scale, size, align_corners=false])
Upsample(scale, mode = :nearest)
```

Upsampling Layer.

## Layer Construction

### Option 1

  * `mode`: Set to `:nearest`, `:linear`, `:bilinear` or `:trilinear`

Exactly one of two keywords must be specified:

  * If `scale` is a number, this applies to all but the last two dimensions (channel and batch) of the input.  It may also be a tuple, to control dimensions individually.
  * Alternatively, keyword `size` accepts a tuple, to directly specify the leading dimensions of the output.

### Option 2

  * If `scale` is a number, this applies to all but the last two dimensions (channel and batch) of the input.  It may also be a tuple, to control dimensions individually.
  * `mode`: Set to `:nearest`, `:bilinear` or `:trilinear`

Currently supported upsampling `mode`s and corresponding NNlib's methods are:

  * `:nearest` -> `NNlib.upsample_nearest`
  * `:bilinear` -> `NNlib.upsample_bilinear`
  * `:trilinear` -> `NNlib.upsample_trilinear`

# Extended Help

## Other Keyword Arguments

  * `align_corners`: If `true`, the corner pixels of the input and output tensors are aligned, and thus preserving the values at those pixels. This only has effect when mode is one of `:bilinear` or `:trilinear`.

## Inputs

  * `x`: For the input dimensions look into the documentation for the corresponding `NNlib` function

      * As a rule of thumb, `:nearest` should work with arrays of arbitrary dimensions
      * `:bilinear` works with 4D Arrays
      * `:trilinear` works with 5D Arrays

## Returns

  * Upsampled Input of size `size` or of size `(I_1 x scale[1], ..., I_N x scale[N], C, N)`
  * Empty `NamedTuple()`
