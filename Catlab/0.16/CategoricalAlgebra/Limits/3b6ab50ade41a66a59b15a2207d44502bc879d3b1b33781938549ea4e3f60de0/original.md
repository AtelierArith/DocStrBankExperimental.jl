Limit of a diagram.

To define limits in a category with objects `Ob`, override the method `limit(::FreeDiagram{Ob})` for general limits or `limit(::D)` with suitable type `D <: FixedShapeFreeDiagram{Ob}` for limits of specific shape, such as products or equalizers.

See also: [`colimit`](@ref)
