```
operator_warn(model::AbstractModel)
operator_warn(model::GenericModel)
```

This function is called on the model whenever two affine expressions are added together without using `destructive_add!`, and at least one of the two expressions has more than 50 terms.

For the case of `Model`, if this function is called more than 20,000 times then a warning is generated once.

This method should only be implemented by developers creating JuMP extensions. It should never be called by users of JuMP.
