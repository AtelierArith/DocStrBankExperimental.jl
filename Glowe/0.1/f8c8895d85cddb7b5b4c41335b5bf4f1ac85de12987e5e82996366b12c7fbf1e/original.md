```
vocab_count(corpus, vocab; max_vocab=100_000, min_count=10, verbose=2)
```

Extracts unigram counts.

# Arguments

  * `corpus::AbstractString` input corpus file path
  * `vocab::AbstractString` output vocabulary file path

# Keyword arguments

  * `verbose::Int` set verbosity: 0, 1 or 2 (default)
  * `max_vocab::Int` upper bound on vocabulary size, i.e. keep the <int> most frequent words. The minimum frequency words are randomly sampled so as to obtain an even distribution over the alphabet.
  * `min_count::Int` lower limit such that words which occur fewer than <int> times are discarded.

# Examples

```
julia> vocab_count("corpus.txt", "vocab.txt", verbose=2, max_vocab=100_000, min_count=10)
```
