シーンの変換を保持します。

## フィールド

  * `parent::Base.RefValue{AbstractPlotting.Transformable}`
  * `translation::Observables.Observable{GeometryBasics.Vec{3, Float32}}`
  * `scale::Observables.Observable{GeometryBasics.Vec{3, Float32}}`
  * `rotation::Observables.Observable{AbstractPlotting.Quaternionf0}`
  * `model::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float32, 16}}`
  * `flip::Observables.Observable{Tuple{Bool, Bool, Bool}}`
  * `align::Observables.Observable{GeometryBasics.Vec{2, Float32}}`
  * `transform_func::Observables.Observable{Any}`
