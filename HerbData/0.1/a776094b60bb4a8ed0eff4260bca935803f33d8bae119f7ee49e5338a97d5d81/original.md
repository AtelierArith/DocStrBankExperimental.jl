```
readdata(directory::AbstractString, lineparser::Function)::Vector{Problem}
```

Reads all files in the given directory and parses them line by line into an  `ExampleProblem` using the given lineparser.

*TODO: Turn this into an iterator that doesn't load all data into memory at initialization.*
