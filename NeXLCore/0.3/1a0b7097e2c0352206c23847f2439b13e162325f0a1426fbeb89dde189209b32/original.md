```
colorize(krs::AbstractVector{<:KRatios}, red::Element, green::Element, blue::Element, normalize=:All[|:Each])
colorize(krs::AbstractVector{<:KRatios}, elms::AbstractVector{Element}, normalize=:All)
```

Create RGB colorized images from up to three `Element`s.  The elements are normalized relative to all `KRatios` in `krs`. The resulting images are scaled by the factor `scale` to allow visualization of trace elements.
