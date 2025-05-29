```
update_labels!(e::Int,model,f_Γ::Function,name::String)
```

Given a tag number `e`, a `CartesianDiscreteModel` or `DistributedDiscreteModel` model, an indicator function `f_Γ`, and a string `name`, label the corresponding vertices, edges, and faces as `name`.

Note: `f_Γ` must recieve a Vector and return a Boolean depending on whether it indicates Γ
