```
@krecord struct MyStruct
    a::Int = 1
    b::Float64
end
```

Macro to define a struct with keyword arguments and `MLStyle.@as_record`, and following generic functions are defined:

  * `copy`
