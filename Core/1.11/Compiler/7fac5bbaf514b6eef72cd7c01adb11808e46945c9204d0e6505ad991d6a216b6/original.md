```
lock_mi_inference(::AbstractInterpreter, mi::MethodInstance)
```

Hint that `mi` is in inference to help accelerate bootstrapping. This is particularly used by `NativeInterpreter` and helps us limit the amount of wasted work we might do when inference is working on initially inferring itself by letting us detect when inference is already in progress and not running a second copy on it. This creates a data-race, but the entry point into this code from C (`jl_type_infer`) already includes detection and restriction on recursion, so it is hopefully mostly a benign problem, since it should really only happen during the first phase of bootstrapping that we encounter this flag.
