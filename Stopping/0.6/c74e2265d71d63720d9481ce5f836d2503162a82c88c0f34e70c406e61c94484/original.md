fill_in!: (NLPStopping version) a function that fill in the required values in the `NLPAtX`.

`fill_in!( :: NLPStopping, :: Union{AbstractVector, Nothing}; fx :: Union{AbstractVector, Nothing} = nothing, gx :: Union{AbstractVector, Nothing} = nothing, Hx :: Union{MatrixType, Nothing} = nothing, cx :: Union{AbstractVector, Nothing} = nothing, Jx :: Union{MatrixType, Nothing} = nothing, lambda :: Union{AbstractVector, Nothing} = nothing, mu :: Union{AbstractVector, Nothing} = nothing, matrix_info :: Bool = true, kwargs...)`
