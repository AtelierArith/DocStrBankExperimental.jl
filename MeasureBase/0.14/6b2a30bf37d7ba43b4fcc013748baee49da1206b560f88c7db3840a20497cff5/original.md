```
struct PushforwardMeasure{F,I,M,VC<:TransformVolCorr} <: AbstractPushforward
    f :: F
    finv :: I
    origin :: M
    volcorr :: VC
end

Users should not call `PushforwardMeasure` directly. Instead call or add
methods to `pushfwd`.
```
