"   simulate(comp::Material, dose::Float64, e0::Float64, θtoa::Float64, Ω::Float64, det::Detector, resp::Matrix{Float64}; noise=false, vargs...)

Compute a simulated X-ray spectrum for the specified composition material.

Arguments:

  * comp: The Material
  * dose: The electron dose in nA⋅s
  * e0:   The beam energy in eV
  * θtoa: The take-off angle in radians
  * Ω:    The detector solid angle in steradians
  * det:  The detector model
  * resp: The detector response

Returns a `Spectrum` struct.
