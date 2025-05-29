```
MLJModels.load(name; pkg=nothing, add=false, verbosity=0, mod=Main)
```

Experimental method. Currently private.

Loads model code into specified module `mod` at run time, as opposed to `@load` which loads coad into calling module at time of invokation.
