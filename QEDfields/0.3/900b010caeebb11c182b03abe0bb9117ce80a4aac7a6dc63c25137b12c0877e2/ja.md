パルス平面波場の抽象基本型。

!!! note "パルス場インターフェース"
    すべてのサブタイプに対して、以下の関数を実装する必要があります。

    ```Julia

    reference_momentum(::AbstractPulsedPlaneWaveField)
    domain(::AbstractPulsedPlaneWaveField)
    pulse_length(::AbstractPulsedPlaneWaveField)
    envelope(::AbstractPulsedPlaneWaveField,x::Real)
    ```

