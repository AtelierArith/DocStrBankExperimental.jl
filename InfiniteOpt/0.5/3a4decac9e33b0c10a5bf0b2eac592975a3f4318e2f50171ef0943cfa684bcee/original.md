```
support_label(data::AbstractMeasureData)::Type{<:AbstractSupportLabel}
```

Return the label stored in `data` associated with its supports. This is intended as en internal method for measure creation and ensures any new supports are added to parameters with such a label. User-defined measure data types should extend this functionif supports are used, otherwise an error is thrown.
