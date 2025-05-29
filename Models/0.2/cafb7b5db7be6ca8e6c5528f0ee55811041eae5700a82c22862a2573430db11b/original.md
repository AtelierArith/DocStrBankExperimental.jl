fit(::Template, output::AbstractMatrix, input::AbstractMatrix, [weights]) -> Model

Fit the [`Template`](@ref) to the `output` and `input` data and return a trained [`Model`](@ref). Convention is that `weights` defaults to `StatsBase.uweights(Float32, size(outputs, 2))`
