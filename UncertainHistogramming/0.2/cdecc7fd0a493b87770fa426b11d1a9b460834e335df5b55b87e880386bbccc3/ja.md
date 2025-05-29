```
setindex!(::ContinuousHistogram, val, ::Type{<: Moment})
```

名前から[`ContinuousHistogram`](@ref)の[`Moment`](@ref)にアクセスするための便利な関数です。

!!! warning
    この機能は内部でのみ使用するべきです。[`ContinuousHistogram`](@ref)の`moments`を直接変更すると、[`push!`](@ref)パイプラインが無効になり、最終的に統計が無効になります。

    しかし、何らかの`dev`理由で必要な場合はここにあります。

