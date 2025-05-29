A `SignedDistanceField` is a uniform sampling of an implicit function. The `bounds` field corresponds to the sampling space intervals on each axis. The `data` field represents the value at each point whose exact location can be rationalized from `bounds`. The type is parameterized by:

  * `N` - The dimensionality of the sampling space.
  * `SpaceT` - the type of the space where we will uniformly sample.
  * `FieldT` - the type resulting from evaluation of the implicit function.

Note that decoupling the space and field types is useful since geometry can be formulated with integers and distances can be measured with floating points.
