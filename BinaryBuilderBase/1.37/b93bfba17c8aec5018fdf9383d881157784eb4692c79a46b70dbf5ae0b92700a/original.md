```
locate(fp::FileProduct, prefix::Prefix;
       platform::AbstractPlatform = HostPlatform(),
       verbose::Bool = false,
       isolate::Bool = false)
```

If the given file exists, return its path.  The `platform` and `isolate` arguments are is ignored here, but included for uniformity.  For ease of use, we support a limited number of custom variable expansions such as `${target}`, and `${nbits}`, so that the detection of files within target-specific folders named things like `/lib32/i686-linux-musl` is simpler.
