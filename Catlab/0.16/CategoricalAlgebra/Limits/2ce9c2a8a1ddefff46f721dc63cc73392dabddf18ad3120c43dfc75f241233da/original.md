Colimit of a diagram.

To define colimits in a category with objects `Ob`, override the method `colimit(::FreeDiagram{Ob})` for general colimits or `colimit(::D)` with suitable type `D <: FixedShapeFreeDiagram{Ob}` for colimits of specific shape, such as coproducts or coequalizers.

See also: [`limit`](@ref)
