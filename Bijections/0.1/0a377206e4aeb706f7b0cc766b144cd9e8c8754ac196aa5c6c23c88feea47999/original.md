`active_inv(b::Bijection)` creates a `Bijection` that is the inverse of `b`. The original `b` and the new `Bijection` returned are tied together so that changes to one immediately affect the other. In this way, the two `Bijection`s remain inverses in perpetuity.

See also `inv`.
