```
CrossValidation(DM::AbstractDataModel)
CrossValidation(DM::AbstractDataModel, keeps::AbstractVector{<:AbstractVector})
```

デフォルトでは、1つを残す交差検証です。代わりに、保持する組み合わせを `keeps` を介して指定できます。
