```julia
struct ScanMatcherPose2{T} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

This is but one incarnation for how radar alignment factor could work, treat it as a starting point.

Notes

  * Stanard `cvt` argument is lambda function to convert incoming images to user convention of image axes,

      * default `cvt` flips image rows so that Pose2 xy-axes corresponds to img[x,y] – i.e. rows down and across from top left corner.
  * Use rescale to resize the incoming images for lower resolution (faster) correlations
  * Both images passed to the construct must have the same type some matrix of type `T`.

## Example

```julia
arp2 = ScanMatcherPose2(img1, img2, 2) # e.g. 2 meters/pixel 
```

See also: [`overlayScanMatcher`](@ref)
