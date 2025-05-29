```
@checked function foo(...)
    rv = ...
    return rv
end
```

Macro for wrapping a function definition returning a status code. Two versions of the function will be generated: `foo`, with the function execution wrapped by an invocation of the `check` function (to be implemented by the caller of this macro), and `unchecked_foo` where no such invocation is present and the status code is returned to the caller.
