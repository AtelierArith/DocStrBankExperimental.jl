Parameters:

  * s::Schema{Name}
  * f::Name

Named Parameters:

  * to::Any = nothing

If `to` is nothing, then this returns the domain of the unique morphism with name `f`, and errors otherwise. If `to` is not nothing, then it should be either an object/attrtype or an iterable of objects/attrtypes, and this should return the domain of the unique morphism with codomain in `to`.
