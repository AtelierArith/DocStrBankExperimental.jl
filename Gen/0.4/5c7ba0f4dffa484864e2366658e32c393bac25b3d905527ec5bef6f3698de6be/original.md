```
arg_grads = gradient(gen_fn::CustomDetermGF, args, retval, retgrad)
```

Return the gradient tuple with respect to the arguments, where `nothing` is for argument(s) whose gradient is not available.
