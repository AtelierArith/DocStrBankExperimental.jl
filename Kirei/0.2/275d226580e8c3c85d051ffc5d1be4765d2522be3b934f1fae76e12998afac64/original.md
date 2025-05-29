```
@kenum EnumName[::BaseType] value1[=x] value2[=y]
@kenum EnumName begin
    value1
    value2
end
@kenum ExistingEnum
```

Macro to define a Julia-style enum that supports MLStyle's patten matching. See `Base.@enum`.
