```
embedded(x)
```

# Arguments

  * `x`: some kind of Markov chain.

# Returns

If the Markv chain is continuous, then it returns the embedded Markov chain. If the Markov chain is discrete, then it returns the given chain, `x`.

# Notes

If the equivalent chain is preffered rather than the embedded chain, then use `DiscreteMarkovChain(x)`.
