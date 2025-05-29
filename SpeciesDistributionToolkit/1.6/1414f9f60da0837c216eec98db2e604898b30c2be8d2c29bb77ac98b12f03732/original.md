SimpleSDMLayers.mask(layer::L, feature::T) where {L<:Union{<:SDMLayer,Vector{<:SDMLayer}}, T <: Union{Feature, FeatureCollection, Polygon, MultiPolygon}}

Returns a copy of the layer by the polygon.
