```
completions(r::ReplCmd, sofar::AbstractString)
```

Obtain a list of `String` completion candidates based on `sofar`. All candidates should begin with `sofar`.

Should this function not be implemented for the specific ReplCmd `r`, `allcompletions(r)` will be called and filter to candidates that begin with `sofar`.

If `r` has subcommands, then the subcommand prefix will be removed and `completions` re-called on the relevant subcommand.
