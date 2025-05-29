```
getndof(model|Element)
getndof(model|Element,class)
getndof(model|Element,(class1,class2,[,...]))
```

where `class` can be any of `:X`, `:U`, `:A`: get the number of dofs of the specified dof-classes (default: all classes) for the variable `model` or the type `Element`.

See also: [`describe`](@ref)
