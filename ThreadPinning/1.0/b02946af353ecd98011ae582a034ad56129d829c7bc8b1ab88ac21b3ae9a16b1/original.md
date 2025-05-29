```
pinthreads_likwidpin(str::AbstractString; onebased = false)
```

Pins Julia threads to CPU-threads based on the given `likwid-pin` compatible string. Checkout the [LIKWID documentation](https://github.com/RRZE-HPC/likwid/wiki/Likwid-Pin) for more information.

If the keyword argument `onebased` is set to `true`, logical indices as well as domain indices start at one instead of zero (likwid-pin default). Note, though, that this doesn't affect the explicit pinning mode where "physical" CPU IDs always start at zero.

**Examples**

  * `pinthreads_likwidpin("S0:0-3")`
  * `pinthreads_likwidpin("M1:0,2,4")`
  * `pinthreads_likwidpin("S:scatter")`
  * `pinthreads_likwidpin("E:N:4:1:2")`
