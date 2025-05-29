```
load_operator(dir,feop::ParamOperator;kwargs...) -> RBOperator
```

Given a FE operator `feop`, load its reduced counterpart stored in the directory `dir`. Throws an error if the reduced operator has not been previously saved to file
