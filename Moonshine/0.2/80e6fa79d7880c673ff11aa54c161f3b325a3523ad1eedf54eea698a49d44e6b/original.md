```
BernoulliMulti
```

Distribution of a 0-1 vector.

# Fields

  * `p::Vector{T}`: probability distribution of the vector. The probability of configuration c = b1 b2 ... bn is the binary representation of the index of its probability in `p`.

# Limitations

Due to implementation, the dimensionality of the distribution cannot exceed the word size of the machine, i.e. `Sys.WORD_SIZE`.
