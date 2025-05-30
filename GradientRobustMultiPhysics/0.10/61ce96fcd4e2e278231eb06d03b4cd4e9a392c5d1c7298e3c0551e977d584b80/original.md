```julia
writeCSV!(
    filename::String,
    Data::Vector{<:GradientRobustMultiPhysics.FEVectorBlock};
    operators,
    names,
    seperator
)

```

Writes the specified FEVectorBlocks into a CSV datafile with the given filename. First d colomuns are the grid coordinates, the remaining columns are filled with the evaluations of the operators where operator[j] is applied to Data[j].
