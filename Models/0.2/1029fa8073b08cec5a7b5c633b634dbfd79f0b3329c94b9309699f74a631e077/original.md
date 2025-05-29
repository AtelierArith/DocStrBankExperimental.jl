Model

A Model is a trained [`Template`](@ref) with which one can [`predict`](@ref) on inputs. Defined as well are the traits:

  * [`output_type`](@ref): [`SingleOutput`](@ref) or [`MultiOutput`](@ref).
  * [`estimate_type`](@ref): [`PointEstimate`](@ref) or [`DistributionEstimate`](@ref).
