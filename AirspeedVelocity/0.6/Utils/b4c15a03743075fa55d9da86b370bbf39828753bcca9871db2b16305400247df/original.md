```
load_results(specs::Vector{PackageSpec}; input_dir::String=".")
```

Load the results from JSON files for each PackageSpec in the `specs` vector. The function assumes that the JSON files are located in the `input_dir` directory and are named as "results_{s}.json" where `s` is equal to `PackageName@Rev`.

The function returns a combined OrderedDict, to be input to the `combined_plots` function.

# Arguments

  * `specs::Vector{PackageSpec}`: Vector of each package revision to be loaded (as `PackageSpec`).
  * `input_dir::String="."`: Directory where the results. Default is current directory.

# Returns

  * `OrderedDict{String,OrderedDict}`: Combined results ready to be passed to the `combined_plots` function.
