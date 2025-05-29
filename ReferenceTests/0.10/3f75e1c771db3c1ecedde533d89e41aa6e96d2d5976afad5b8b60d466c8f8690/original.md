```
psnr_equality(threshold=25) -> f
```

Generates an equality comparison function in terms of Peak Signal-to-Noise Ratio (PSNR).

The return function `f` accepts two images `reference` and `actual` as its inputs; `f(reference, actual) == true` if `psnr(reference, actual) >= threshold`.

This function is useful for image comparison; higher PSNR means higher image similarity. Hence if you want to loose the equality test creterion, you can use a **smaller** threshold value, e.g.,

```julia
@test_reference "references/camera.png" testimage("cameraman") by=psnr_equality(20)
```
