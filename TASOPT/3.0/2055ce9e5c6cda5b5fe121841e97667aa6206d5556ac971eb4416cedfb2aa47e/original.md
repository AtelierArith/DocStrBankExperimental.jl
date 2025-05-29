```
generate_par_indname(par_suffix::String)
```

generates a vector that contains variable names of par_array indices, "mapping"  the index to its name as declared in `index.inc` and found in the global scope

ex:

```@example par_indname
    using TASOPT
    #note that igRange = 1 (from `index.inc`)

    parg_indname = generate_par_indname("g")
    parg_indname[1]
```

!!! details "🔃 Inputs and Outputs"
    **Inputs:**

      * `par_suffix::String`: suffix of a par array (e.g., "g" for "parg"),

    **Outputs:**

      * `par_indname::Vector{String}`: vector of strings with entries corresponding to the index variable names

