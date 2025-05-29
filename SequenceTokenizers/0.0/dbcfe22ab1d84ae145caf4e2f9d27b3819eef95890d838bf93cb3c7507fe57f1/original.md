```
onehot_batch(tokenizer::AbstractSequenceTokenizer, batch::AbstractVector{UInt32})
```

Convert a batch of tokenized sequences to one-hot representations.

This function takes a vector of token indices and converts it into a one-hot encoded representation using the alphabet of the provided tokenizer.

# Arguments

  * `tokenizer::AbstractSequenceTokenizer`: The tokenizer used for the sequences. Its length

determines the size of the one-hot encoding dimension.

  * `batch::AbstractVector{UInt32}`: A vector of token indices to be converted to

one-hot representation.

# Returns

  * `OneHotArray`: A one-hot encoded representation of the input batch. The resulting

array will have dimensions (length(tokenizer), length(batch)).

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
tokenized_sequence = [2, 3, 1, 4]  # Corresponds to ['a', 'b', 'x', 'c']
onehot = onehot_batch(tokenizer, tokenized_sequence)
println(size(onehot))  # Output: (4, 4)
println(onehot[:, 1])  # Output: [0, 1, 0, 0]
```

# Note

This function assumes that all indices in the input batch are valid for the tokenizer's alphabet. Indices outside the valid range may result in errors or unexpected behavior.

# See also

  * [`SequenceTokenizer`](@ref): The tokenizer struct used to create the input batch.
  * [`onecold_batch`](@ref): The inverse operation, converting one-hot representations

back to token indices.
