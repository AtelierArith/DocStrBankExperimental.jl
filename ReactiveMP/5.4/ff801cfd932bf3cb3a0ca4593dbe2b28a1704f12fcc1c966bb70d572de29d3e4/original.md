```
FormConstraintCheckEach
```

This form constraint check strategy checks functional form of the last messages product in the equality chain.  Usually if a variable has been connected to multiple nodes we want to perform multiple `prod` to obtain a posterior marginal. With this form check strategy `constrain_form` function will be executed only once after all subsequenct `prod` functions have been executed.
