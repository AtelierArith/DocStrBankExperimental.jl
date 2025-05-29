```
PrescribedPhotosyntheticallyActiveRadiation(fields)
```

`PrescribedPhotosyntheticallyActiveRadiation` returns "prescribed" PAR fields which are user specified, e.g. they may be `FunctionField`s or  `ConstantField`s.

`fields` may either be an `AbstractField` or a `NamedTuple` of names and  fields which will be returned in `biogeochemical_auxiliary_fields`, if only one field is present the field will be named `PAR`.
