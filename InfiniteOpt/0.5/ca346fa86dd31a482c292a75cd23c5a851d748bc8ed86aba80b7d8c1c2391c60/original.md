```
Measure{T <: JuMP.AbstractJuMPScalar, V <: AbstractMeasureData}
```

A `DataType` for measure abstractions. The abstraction is determined by `data` and is enacted on `func` when the measure is evaluated (expended).

**Fields**

  * `func::T` The `InfiniteOpt` expression to be measured.
  * `data::V` Data of the abstraction as described in a `AbstractMeasureData`           concrete subtype.
  * `object_nums::Vector{Int}`: The parameter object numbers of the evaluated                             measure expression (i.e., the object numbers of                             `func` excluding those that belong to `data`).
  * `parameter_nums::Vector{Int}`: The parameter numbers that parameterize the                                evaluated measure expression. (i.e., the                                parameter numbers of `func` excluding those                                that belong to `data`).
  * `constant_func::Bool`: Indicates if `func` is not parameterized by the infinite                        parameters in `data`. (i.e., do the object numbers of                        `func` and `data` have no intersection?) This is useful                        to enable analytic evaluations if possible.
