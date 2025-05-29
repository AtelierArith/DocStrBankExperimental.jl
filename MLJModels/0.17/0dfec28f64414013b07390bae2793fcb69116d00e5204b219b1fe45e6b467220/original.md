```
@load ModelName pkg=nothing verbosity=0 add=false
```

Import the model type the model named in the first argument into the calling module, specfying `pkg` in the case of an ambiguous name (to packages providing a model type with the same name). Returns the model type.

**Warning** In older versions of MLJ/MLJModels, `@load` returned an *instance* instead.

To automatically add required interface packages to the current environment, specify `add=true`. For interactive loading, use `@iload` instead.

### Examples

```
Tree = @load DecisionTreeRegressor
tree = Tree()
tree2 = Tree(min_samples_split=6)

SVM = @load SVC pkg=LIBSVM
svm = SVM()
```

See also [`@iload`](@ref)
