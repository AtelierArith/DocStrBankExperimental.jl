**単変量**

```
samplePCE(n::Int,x::AbstractVector{<:Real},op::AbstractOrthoPoly;method::String="adaptiverejection")
```

[`sampleMeasure`](@ref) と [`evaluatePCE`](@ref) を組み合わせます。つまり、最初に測度から `n` サンプルを引き出し、その後それらのサンプルに対して PCE を評価します。

**多変量**

```
samplePCE(n::Int,x::AbstractVector{<:Real},mop::MultiOrthoPoly;method::Vector{String}=["adaptiverejection" for i=1:length(mop.meas.name)])
```
