```
PrescribedPhotosyntheticallyActiveRadiation(fields)
```

`PrescribedPhotosyntheticallyActiveRadiation` は、ユーザーが指定した「処方された」PARフィールドを返します。例えば、`FunctionField` または `ConstantField` である可能性があります。

`fields` は `AbstractField` または名前とフィールドの `NamedTuple` である場合があり、`biogeochemical_auxiliary_fields` に返されます。フィールドが1つだけ存在する場合、そのフィールドは `PAR` と名付けられます。
