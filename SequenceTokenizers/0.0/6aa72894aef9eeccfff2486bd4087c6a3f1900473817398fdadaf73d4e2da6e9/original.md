```
onecold_batch(tokenizer::AbstractSequenceTokenizer, onehot_batch::OneHotArray)
```

Convert a one-hot representation back to tokenized sequences.

# Arguments

  * `tokenizer::AbstractSequenceTokenizer`: The tokenizer used for the sequences
  * `onehot_batch::OneHotArray`: A OneHotArray representing the one-hot encoding of sequences

# Returns

A matrix of indices representing the tokenized sequences

# Example

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
sequences = [['a', 'b'], ['c', 'a', 'b']]
tokenized = tokenizer(sequences)
onehot = onehot_batch(tokenizer, tokenized)
recovered = onecold_batch(tokenizer, onehot)
# Recovered result is batched therefore it remains padded
println(recovered == ['a' 'c'; 'b' 'a'; 'x' 'b']) # Output: true
```
