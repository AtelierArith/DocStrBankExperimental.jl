Holds the transformations for Scenes.

## Fields

  * `parent::Base.RefValue{Makie.Transformation}`
  * `translation::Observables.Observable{GeometryBasics.Vec{3, Float32}}`
  * `scale::Observables.Observable{GeometryBasics.Vec{3, Float32}}`
  * `rotation::Observables.Observable{Makie.Quaternionf}`
  * `model::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float32, 16}}`
  * `parent_model::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float32, 16}}`
  * `transform_func::Observables.Observable{Any}`
