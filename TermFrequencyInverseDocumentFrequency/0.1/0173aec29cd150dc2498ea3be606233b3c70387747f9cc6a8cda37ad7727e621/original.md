```
inverse_document_frequencies(term_matrix)
```

Calculate the smoothed inverse document frequencies as `log.((1 + ndocuments)./(1 .+ df)) .+ 1` where `df` is the document frequency. The constant `1` in the numerator and denominator corresponds to an extra document containing each word in the vocabulary once, and prevents division by zero errors.
