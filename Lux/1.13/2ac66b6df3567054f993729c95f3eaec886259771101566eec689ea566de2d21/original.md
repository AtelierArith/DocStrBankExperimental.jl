```
Embedding(in_dims => out_dims; init_weight=rand32)
```

A lookup table that stores embeddings of dimension `out_dims` for a vocabulary of size `in_dims`. When the vocabulary is multi-dimensional, the input is expected to be a tuple of Cartesian indices.

This layer is often used to store word embeddings and retrieve them using indices.

## Arguments

  * `in_dims`: number(s) of input dimensions
  * `out_dims`: number of output dimensions

## Keyword Arguments

  * `init_weight`: initializer for the weight matrix (`weight = init_weight(rng, out_dims, in_dims...)`)

## Input

  * Integer OR
  * Abstract Vector of Integers OR
  * Abstract Array of Integers OR
  * Tuple of Integers OR
  * Tuple of Abstract Vectors of Integers OR
  * Tuple of Abstract Arrays of Integers

## Returns

  * Returns the embedding corresponding to each index in the input. For an N dimensional input, an N + 1 dimensional output is returned.
  * Empty `NamedTuple()`

!!! warning "Gradients with Tracker.jl

```
Tracker.jl produces incorrect gradients for this layer if indices in the input are
repeated. Don't use this layer with Tracker.jl if you need to compute gradients.
```
