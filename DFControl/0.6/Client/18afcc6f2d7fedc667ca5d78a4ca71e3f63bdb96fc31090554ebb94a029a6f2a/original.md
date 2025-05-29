```
outputdata(job::Job; server = job.server, calcs::Vector{String}=String[])
```

Finds the output files for each of the calculations of a [`Job`](@ref), and groups all the parsed data into a dictionary.
