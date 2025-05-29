```
binarize(img::AbstractArray{<:Number}, threshold::Real=0.5) -> BitArray
```

Convert an image or array to a binary (0/1) mask using the given threshold.

If `img` is a color image (3rd dimension size 3), it is converted to grayscale using the mean across channels. The threshold is applied such that values >= threshold are set to 1, others to 0.

# Arguments

  * `img`: Input array (2D or 3D).
  * `threshold`: Threshold value (default 0.5).

# Returns

  * `BitArray`: Binary mask.
