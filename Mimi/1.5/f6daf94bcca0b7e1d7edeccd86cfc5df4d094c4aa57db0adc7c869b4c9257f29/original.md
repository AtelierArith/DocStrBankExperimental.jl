```
set_param!(ref::ComponentReference, name::Symbol, value)
```

Set a component parameter as `set_param!(reference, name, value)`. This creates a unique name :compname_paramname in the model's model parameter list,  and sets the parameter only in the referenced component to that value.
