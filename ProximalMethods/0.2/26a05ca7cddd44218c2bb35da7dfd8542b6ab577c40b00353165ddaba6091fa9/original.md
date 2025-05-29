```
block_soft_thresh(x, λ)
```

Compute block soft thresholding operator with scaling parameter `λ` at `x`, proximal operator of the $ℓ₂$-norm.

#### Arguments

  * `x::AbstractVector`	: input (n x 1)
  * `λ::Real`			: scaling parameter

#### Returns

  * `y::AbstractVector`	: block soft thresholded value (n x 1)
