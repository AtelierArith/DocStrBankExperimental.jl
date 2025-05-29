```
humann_renorm(comm::AbstractDataFrame; units::String="cpm")
```

Wrapper for `humann_renorm_table` script, to renormalize from RPKM (reads per kilobase per million) to "cpm" (counts per million) or "relab" (relative abundance).

Requires installation of [`humann`](https://github.com/biobakery/humann) available in `ENV["PATH"]`. See "[Using Conda](@ref using-conda)" for more information.
