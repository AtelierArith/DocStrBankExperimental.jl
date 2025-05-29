```
hyperparam([T::Type,] name; prefix="SM_HP_"))
```

Load the hyperparameter with the given `name` from the environment variable named with the name in uppercase, and prefixed with `prefix`. If the type `T` is passed then it will be parsed as that type, otherwise it will take a guess at the type chosing the first that passes successfully from `Bool`, `Int`, then `Float` then `String`

Also stores the hyperparameter and its value in the global `HYPERPARAMETERS` dictionary. This function is generally expected to be used with SageMaker, and supplies the default prefix for it.

```jldoctest
using Hyperparameters
ENV["HP_POWER_LEVEL"] = "9001"
hyperparam(:power_level; prefix="HP_")

# output
9001.0
```
