Check that `CartesianFrame3D` `f1` is one of `f2s`.

Note that if `f2s` is a `CartesianFrame3D`, then `f1` and `f2s` are simply checked for equality.

Throws an `ArgumentError` if `f1` is not among `f2s` when bounds checks are enabled. `@framecheck` is a no-op when bounds checks are disabled.
