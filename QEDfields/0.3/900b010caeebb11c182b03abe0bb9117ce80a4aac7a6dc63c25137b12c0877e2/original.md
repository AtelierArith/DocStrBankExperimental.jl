Abstract base type for pulsed plane-wave fields.

!!! note "Pulsed field interface"
    For every subtype, the following functions need to be implemented.

    ```Julia

    reference_momentum(::AbstractPulsedPlaneWaveField)
    domain(::AbstractPulsedPlaneWaveField)
    pulse_length(::AbstractPulsedPlaneWaveField)
    envelope(::AbstractPulsedPlaneWaveField,x::Real)
    ```

