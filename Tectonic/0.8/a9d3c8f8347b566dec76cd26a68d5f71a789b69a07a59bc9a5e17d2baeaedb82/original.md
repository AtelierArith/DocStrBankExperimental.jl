```
tectonic(f)
```

Call function `f` with the *tectonic* binary path as argument.

```julia
tectonic() do bin
    run(`$bin file.tex`)
end
```

All required setup and clean-up to run the binary correctly is done automatically.

!!! note
    Currently nothing is needed to be done to run the binary, but this may change in future and this provides a future-proof interface to the package.

