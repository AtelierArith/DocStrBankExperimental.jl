```
locate(lp::LibraryProduct, prefix::Prefix;
       env::Dict{String,String},
       verbose::Bool = false)
```

If the given library exists (under any reasonable name) and is `dlopen()`able, (assuming it was built for the current platform) return its location.  Note that the `dlopen()` test is only run if the current platform matches the given `platform` keyword argument, as cross-compiled libraries cannot be `dlopen()`ed on foreign platforms.
