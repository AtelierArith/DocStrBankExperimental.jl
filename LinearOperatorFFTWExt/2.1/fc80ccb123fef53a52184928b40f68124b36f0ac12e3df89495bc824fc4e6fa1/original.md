DCTOpImpl(T::Type, shape::Tuple, dcttype=2)

returns a `DCTOpImpl <: AbstractLinearOperator` which performs a DCT on a given input array.

# Arguments:

  * `T::Type`       - type of the array to transform
  * `shape::Tuple`  - size of the array to transform
  * `dcttype`       - type of DCT (currently `2` and `4` are supported)
