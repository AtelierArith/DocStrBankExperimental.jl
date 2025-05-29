```julia
struct AprilTag
```

## Represents the detected April tag.

Fields:

  * `family::String`: The family of the tag.
  * `id::Int64`: The decoded ID of the tag.
  * `hamming::Int64`: How many error bits were corrected? Note: accepting large numbers of corrected errors leads to greatly increased false positive rates. NOTE: As of this implementation, the detector cannot detect tags with a Hamming distance greater than 2.
  * `decision_margin::Float32`: A measure of the quality of the binary decoding process: the average difference between the intensity of a data bit versus the decision threshold. Higher numbers roughly indicate better decodes. This is a reasonable measure of detection accuracy only for very small tags– not effective for larger tags (where we could have sampled anywhere within a bit cell and still gotten a good detection.)
  * `H::Matrix{Float64}`: The 3x3 homography matrix describing the projection from an "ideal" tag (with corners at (-1,1), (1,1), (1,-1), and (-1,-1)) to pixels in the image.
  * `c::Vector{Float64}`: The center of the detection in image pixel coordinates
  * `p::Vector{Vector{Float64}}`: The corners of the tag in image pixel coordinates. These always wrap counter-clock wise around the tag.
