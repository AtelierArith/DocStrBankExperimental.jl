```
NeXLMatrixCorrection.estimatecoating(fr::FitResult, substrate::Material, coating::Material, cxr::CharXRay, mc::Type{<:MatrixCorrection}=XPP)::Film
```

Estimate the mass-thickness of `coating` on bulk `substrate` using the X-ray `cxr` for which there is KRatio in `fr`.  The result is assigned to the properties of `fr` so that it can be account for in the matrix correction process.

This method is intended for use on standards where the substrate composition is known a priori.
