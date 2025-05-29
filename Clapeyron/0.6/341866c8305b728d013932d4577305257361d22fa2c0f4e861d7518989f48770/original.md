```
@newmodel name parent paramstype [sitemodel = true]
```

This is exactly the same as the above but for non-GC models. All group parameters are absent in this struct. The sites are associated to the main component rather than the groups, and the respective fieldnames are named correspondingly.

You can pass an optional bool indicating if you want to use sites with this model or not. defaults to `true`

## Example

```julia
struct MySAFTParam
    a::SingleParam{Float64}
    b::SingleParam{Float64}
    epsilon_assoc::AssocParam{Float64}
    bondvol::AssocParam{Float64}
end

@newmodel MySAFT SAFTModel MySAFTParam #defines a model, with association sites

struct MyModelParam
    a::SingleParam{Float64}
    b::SingleParam{Float64}
end

@newmodel MyModel EoSModel MyModelParam false #defines a model without sites
```
