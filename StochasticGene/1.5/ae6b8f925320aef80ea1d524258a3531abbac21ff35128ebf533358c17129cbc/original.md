```
readrates(infolder::String, label::String, gene::String, G::Int, R::Int, S::Int, insertstep::Int, nalleles::Int, ratetype::String="median")
```

Read in rates from a file.

# Arguments

  * `infolder::String`: Folder holding rate files.
  * `label::String`: Label for rate files.
  * `gene::String`: Gene name.
  * `G::Int`: Number of G states.
  * `R::Int`: Number of R steps.
  * `S::Int`: Number of splice states.
  * `insertstep::Int`: R step where splicing starts.
  * `nalleles::Int`: Number of alleles.
  * `ratetype::String`: Type of rate to read. Defaults to `"median"`.

# Returns

  * `Array{Float64, 2}`: The read rates from the file.

# Examples

```julia rates = readrates("data", "label", "gene", 3, 5, 2, 1, 2, "mean")
