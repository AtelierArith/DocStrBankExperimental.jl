```
struct PushforwardMeasure{FF,IF,MU,VC<:TransformVolCorr} <: AbstractPushforward
    f :: FF
    inv_f :: IF
    origin :: MU
    volcorr :: VC
end
```
