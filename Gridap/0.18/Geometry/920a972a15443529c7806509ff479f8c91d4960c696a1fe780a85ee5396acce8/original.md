CartesianDiscreteModel(desc::CartesianDescriptor{D,T,F},                           cmin::CartesianIndex,                           cmax::CartesianIndex)

Builds a CartesianDiscreteModel object which represents a subgrid of   a (larger) grid represented by desc. This subgrid is described by its   D-dimensional minimum (cmin) and maximum (cmax) CartesianIndex   identifiers.
