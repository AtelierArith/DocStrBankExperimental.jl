```
sorted_rings(s, ℓₘₐₓ, [T=Float64])
```

Compute locations of a series of rings labelled by $j ∈ |s|:ℓₘₐₓ$ (analogous to $ℓ$), where each ring will contain $k = 2j+1$ (analogous to $m$) pixels distributed evenly around the ring.  These rings are then sorted, so that the ring with the most pixels ($j = ℓₘₐₓ$) is closest to the equator, and the next-largest ring is placed just above or below the equator (depending on the sign of $s$), the next just below or above, and so on.  This is generally a fairly good first guess when minimizing the condition number of matrices used to solve for mode weights from function values.  In particular, I use this to initialize the Minimal algorithm, which is then fed into an optimizer to fine-tune the positions of the rings.

This function does not provide the individual pixels; it just provides the colatitude values of the rings on which the pixels will be placed.  The pixels themselves are provided by [`sorted_ring_pixels`](@ref).
