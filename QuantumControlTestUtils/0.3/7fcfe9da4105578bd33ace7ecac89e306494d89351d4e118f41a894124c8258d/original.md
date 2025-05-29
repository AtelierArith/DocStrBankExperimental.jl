Generate an HTML report for existing coverage data.

```julia
generate_coverage_html(
    paths=["src", "ext"]; root=pwd(), covdir="coverage", genhtml="genhtml"
)
```

creates a folder `covdir` in `root` and use the external `genhtml` program to write an HTML coverage report into that folder.
