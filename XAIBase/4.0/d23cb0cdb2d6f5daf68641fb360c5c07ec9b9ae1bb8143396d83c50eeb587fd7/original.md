Abstract super type of all feature selectors in XAIBase.

Feature selectors are expected to be callable and to return a vector of `CartesianIndices` for each selected feature.

## Note

The XAIBase interface currently assumes that features have either 2 or 4 dimensions (`(features, batchsize)` or `(width, height, features, batchsize)`).

It also assumes that the batch dimension is the last dimension of the feature.
