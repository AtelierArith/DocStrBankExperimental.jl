```
ADLChargeDriftModel{T <: SSDFloat, M <: AbstractDriftMaterial, N, TM <: AbstractTemperatureModel{T}} <: AbstractChargeDriftModel{T}
```

Charge drift model for electrons and holes based on the AGATA Detector Library. Find a detailed description of the calculations in [ADL Charge Drift Model](@ref).

## Fields

  * `electrons::CarrierParameters{T}`: Parameters to describe the electron drift along the <100> and <111> axes.
  * `holes::CarrierParameters{T}`: Parameters to describe the hole drift along the <100> and <111> axes.
  * `crystal_orientation::SMatrix{3,3,T,9}`: Rotation matrix that transforms the global coordinate system to the crystal coordinate system given by the <100>, <010> and <001> axes of the crystal.
  * `γ::SVector{N,SMatrix{3,3,T,9}}`: Reciprocal mass tensors to the `N` valleys of the conduction band.
  * `parameters::ADLParameters{T}`: Parameters needed for the calculation of the electron drift velocity.
  * `temperaturemodel::TM`: Models to scale the resulting drift velocities with respect to temperature

See also [`CarrierParameters`](@ref).
