```
FormConstraintCheckEach
```

This form constraint check strategy checks functional form of the messages product after each product in an equality chain.  Usually if a variable has been connected to multiple nodes we want to perform multiple `prod` to obtain a posterior marginal. With this form check strategy `constrain_form` function will be executed after each subsequent `prod` function.
