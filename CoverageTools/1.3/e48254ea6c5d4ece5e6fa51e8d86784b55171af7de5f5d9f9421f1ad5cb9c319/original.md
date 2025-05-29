```
amend_coverage_from_src!(coverage::Vector{CovCount}, srcname)
amend_coverage_from_src!(fc::FileCoverage)
```

The code coverage functionality in Julia only reports lines that have been compiled. Unused functions (or discarded lines) therefore may be incorrectly recorded as `nothing` but should instead be 0. This function takes an existing result and updates the coverage vector in-place to mark source lines that may be inside a function.
