```
update_param!(ref::ComponentReference, name::Symbol, value)
```

Update a component parameter as `update_param!(reference, name, value)`. This uses the unique name :compname_paramname in the model's model parameter list,  and updates the parameter only in the referenced component to that value.
