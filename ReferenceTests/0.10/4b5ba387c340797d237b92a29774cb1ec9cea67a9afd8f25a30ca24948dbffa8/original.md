```
@test_reference filename expr [by] [kw...]
```

Tests that the expression `expr` with reference `filename` using equality test strategy `by`.

The pipeline of `test_reference` is:

1. preprocess `expr`
2. read and preprocess `filename` via FileIO.jl
3. compare the results using `by`
4. if test fails in an interactive session (e.g, `include(test/runtests.jl)`), an interactive dialog will be trigered.

Arguments:

  * `filename::String`: *relative* path to the file that contains the macro invocation.
  * `expr`: the actual content used to compare.
  * `by`: the equality test function. By default it is `isequal` if not explicitly stated.
  * `format`: Force reading the file using a specific format

# Types

The file-extension of `filename`, as well as the type of the result of evaluating `expr`, determine how contents are processed and compared. The contents is treated as:

  * Images when `expr` is an image type, i.e., `AbstractArray{<:Colorant}`;
  * SHA256 when `filename` endswith `*.sha256`;
  * Any file-type which FileIO.jl handles and with the proper backend loaded;
  * Text as a fallback.

## Any FileIO.jl handled filetype

Any file-types which can be read by [FileIO.jl](https://github.com/JuliaIO/FileIO.jl) can be used. Note that most Julia values can be stored using packages such as, e.g., [BSON.jl](https://github.com/JuliaIO/BSON.jl) or [JLD](https://github.com/JuliaIO/JLD.jl) and can thus be used in reference-tests.

## Images

Images are compared *approximately* using a different `by` to ignore most encoding and decoding errors. The default function is generated from [`psnr_equality`](@ref).

The file can be either common image files (e.g., `*.png`), which are handled by `FileIO`, or text-coded `*.txt` files, which is handled by `ImageInTerminal`. Text-coded image has less storage requirements and also allows to view the reference file in a simple terminal using `cat`.

## SHA256

The hash of the `expr` and content of `filename` are compared.

!!! tip
    This is useful for a convenient low-storage way of making sure that the return value doesn't change for selected test cases.


## Fallback

Simply test the equality of `expr` and the contents of `filename` without any preprocessing. Note that reading `filename` will return a `String`.

# Examples

```julia
# compare text-file against string representation of a value
@test_reference "stringtest1.txt" collect(1:20)

# test number with absolute tolerance 10
@test_reference "references/string3.txt" 1338 by=(ref, x)->isapprox(ref, x; atol=10)

# store a floating point array ar in BSON-file and compare it back.
# Note that a Dict is needed and the custom comparison function.
using BSON
comp(d1, d2) = keys(d1)==keys(d2) &&
    all([ v1≈v2 for (v1,v2) in zip(values(d1), values(d2))])
@test_reference "reftest-files/X.bson" Dict(:ar=>[1, pi, 4.5]) by=comp

# store as string using ImageInTerminal with encoding size (5,10)
using TestImages
@test_reference "camera.txt" testimage("cameraman") size=(5,10)

# using folders in the relative path is allowed
@test_reference "references/camera.png" testimage("cameraman")

# Images can also be stored as hash. Note however that this
# can only check for equality (no tolerance possible)
@test_reference "references/camera.sha256" testimage("cameraman")

# test images with custom Peak Signal-to-Noise Ratio (psnr) threshold
@test_reference "references/camera.png" testimage("cameraman") by=psnr_equality(20)
```
