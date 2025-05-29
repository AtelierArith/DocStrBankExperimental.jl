Parameters:

  * s::Schema{Name}

Named Parameters:

  * just_names::Bool=false
  * from::Any = nothing
  * to::Any = nothing

Defaults to returning an iterable of tuples `(f,x,y)` where `f` is the name of a homomorphism and `x` and `y` are its domain and codomain respectively.

If `just_names` is true, then it just returns the `f`s.

If `from` is not nothing then it should be either an object or an iterable of objects; this then filters to only morphisms that have domain in `from`. Mutatis mutandis for `to`.
