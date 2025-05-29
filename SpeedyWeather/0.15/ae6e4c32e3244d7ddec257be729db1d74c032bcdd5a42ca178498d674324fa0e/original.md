Particle with location lon (longitude), lat (latitude) and σ (vertical coordinate). Longitude is assumed to be in [0,360˚E), latitude in [-90˚,90˚N] and σ in [0,1] but not strictly enforced at creation, see `mod(::Particle)` and `ismod(::Particle)`. A particle is either active or inactive, determined by the Boolean in it's 2nd type parameter. By default, a particle is active, of number format DEFAULT_NF and at 0˚N, 0˚E, σ=0.

  * `lon::AbstractFloat`: longitude in [0,360˚]
  * `lat::AbstractFloat`: latitude [-90˚,90˚]
  * `σ::AbstractFloat`: vertical sigma coordinate [0 (top) to 1 (surface)]
