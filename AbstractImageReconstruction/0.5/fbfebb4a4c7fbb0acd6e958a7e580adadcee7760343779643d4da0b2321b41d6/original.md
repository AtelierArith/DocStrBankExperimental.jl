```
toDictValue!(dict, plan::RecoPlan)
```

Adds the properties of `plan` to `dict` using `toDictValue` for each not missing field. Additionally, adds each listener::AbstractPlanListener to the dict.
