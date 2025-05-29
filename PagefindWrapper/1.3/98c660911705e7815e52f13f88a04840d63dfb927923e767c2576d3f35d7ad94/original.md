```
pagefind(; extended::Bool=false)
```

Return a `Cmd` object for the `pagefind` binary. If `extended` is `true` then the `pagefind_extended` binary will be returned. Note that the extended version of the binary is a lazy artifact and will only be downloaded when the `Cmd` is run for the first time.
