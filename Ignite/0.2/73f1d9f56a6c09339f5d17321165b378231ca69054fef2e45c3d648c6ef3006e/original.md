Filter the input `event` to fire conditionally:

Inputs:

  * `event::AbstractFiringEvent`: event to be filtered.
  * `event_filter::Any`: A event_filter function `(::Engine, ::AbstractFiringEvent) -> Bool` returning `true` if the filtered event should be fired.
  * `every::Union{Int, <:AbstractVector{Int}}`: the period(s) in which the filtered event should be fired; see [`every_filter`](@ref).
  * `once::Union{Int, <:AbstractVector{Int}}`: the point(s) at which the filtered event should be fired; see [`once_filter`](@ref).
