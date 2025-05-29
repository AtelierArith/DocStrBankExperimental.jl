Abstract super type of all output selectors in XAIBase.

Output selectors are expected to be callable and to return a vector of `CartesianIndex` of the selected outputs.

## Note

XAIBase assumes that the batch dimension is the last dimension of the output.
