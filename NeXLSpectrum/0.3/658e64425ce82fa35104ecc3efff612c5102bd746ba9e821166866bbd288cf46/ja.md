```
tophatfilter(
    charLabel::Union{CharXRayLabel,EscapeLabel, ReferenceLabel}
    filt::TopHatFilter{T},
    scale::T = one(T),
    tol::T = (T==Float32 ? 1.0f-5 : 1.0e-6)
)::FilteredReference
```

参照スペクトル上のROIをフィルタリングするためのものです。指定されたフィルタでスペクトルの一部を処理します。シンプルなエッジベースのバックグラウンドモデルを使用します。

```
tophatfilter(
    labels::AbstractVector{ReferenceLabel},
    filt::TopHatFilter{T},
    scale::T = one(T),
    tol::T = (T==Float32 ? 1.0f-5 : 1.0e-6)
)::Vector{FilteredReference{T}}
```
