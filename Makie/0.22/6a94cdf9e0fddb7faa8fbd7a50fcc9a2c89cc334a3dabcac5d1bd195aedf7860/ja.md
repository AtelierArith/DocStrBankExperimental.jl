シーンの変換を保持します。

## フィールド

  * `parent::Base.RefValue{Makie.Transformation}`
  * `translation::Observables.Observable{GeometryBasics.Vec{3, Float64}}`
  * `scale::Observables.Observable{GeometryBasics.Vec{3, Float64}}`
  * `rotation::Observables.Observable{Makie.Quaternionf}`
  * `origin::Observables.Observable{GeometryBasics.Vec{3, Float64}}`
  * `model::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float64, 16}}`
  * `parent_model::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float64, 16}}`
  * `transform_func::Observables.Observable{Any}`
