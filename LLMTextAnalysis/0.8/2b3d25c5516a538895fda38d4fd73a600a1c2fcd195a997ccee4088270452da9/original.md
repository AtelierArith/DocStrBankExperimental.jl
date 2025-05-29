```
(spectrum::TrainedSpectrum)(index::AbstractDocumentIndex; check_index::Bool = true)
```

A method definition that allows a `TrainedSpectrum` object to be called as a function to score documents in an `index`. This method delegates to the `score` function.

The score reflects how closely each document aligns with each of the ends of the trained spectrum.  Scores are left-to-right, ie, a score closer to 0 indicates a higher alignment to `spectrum.spectrum[1]` and a score closer to 1 indicates a higher alignment to `spectrum.spectrum[2]`.

# Arguments

  * `index::AbstractDocumentIndex`: The index containing the documents to be scored.
  * `check_index::Bool` (optional): If `true`, performs a check to ensure that the index ID matches the one used in the spectrum training. Defaults to `true`.

# Returns

  * A vector of scores in the range [0, 1], each corresponding to a document in the index.

# Example

```julia
# Assuming `index` and `spectrum` are predefined
scores = spectrum(index)
```

This method provides a convenient and intuitive way to apply a trained spectrum model to a document index for scoring.
