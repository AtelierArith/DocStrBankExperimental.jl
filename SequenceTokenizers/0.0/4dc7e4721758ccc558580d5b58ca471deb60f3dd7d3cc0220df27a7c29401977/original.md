```
SequenceTokenizers
```

A module for tokenizing sequences of symbols into numerical indices and vice versa. This module provides functionality for creating tokenizers, encoding sequences, and working with one-hot representations of tokenized data.

# Exports

  * `SequenceTokenizer`: A struct for tokenizing sequences
  * `onehot_batch`: Convert tokenized sequences to one-hot representations
  * `onecold_batch`: Convert one-hot representations back to tokenized sequences

# Example

```julia
using SequenceTokenizers

# Create a tokenizer for DNA sequences
dna_alphabet = ['A', 'C', 'G', 'T']
tokenizer = SequenceTokenizer(dna_alphabet, 'N')

# Tokenize a sequence
seq = "ACGTACGT"
tokenized = tokenizer(seq)

# Convert to one-hot representation
onehot = onehot_batch(tokenizer, tokenized)

# Convert back to tokens
recovered = onecold_batch(tokenizer, onehot)
```
