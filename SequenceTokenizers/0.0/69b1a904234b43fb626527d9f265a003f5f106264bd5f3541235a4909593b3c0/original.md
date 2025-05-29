```
onehot_batch(tokenizer::SequenceTokenizer, batch::AbstractMatrix{UInt32})
```

Convert a batch of tokenized sequences to one-hot representations.

# Arguments

  * `tokenizer::SequenceTokenizer`: The tokenizer used for the sequences
  * `batch::AbstractMatrix{UInt32}`: A matrix of tokenized sequences

# Returns

A OneHotArray representing the one-hot encoding of the input batch

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
sequences = [["a", "b"], ["c", "a", "b"]]
tokenized = tokenizer(sequences)
onehot = onehot_batch(tokenizer, tokenized)
println(size(onehot))  # Output: (4, 3, 2)
```
