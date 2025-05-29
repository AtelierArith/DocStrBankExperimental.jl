```
@cuprintf("%Fmt", args...)
```

Print a formatted string in device context on the host standard output.

Note that this is not a fully C-compliant `printf` implementation; see the CUDA documentation for supported options and inputs.

Also beware that it is an untyped, and unforgiving `printf` implementation. Type widths need to match, eg. printing a 64-bit Julia integer requires the `%ld` formatting string.
