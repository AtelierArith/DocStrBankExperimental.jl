```
score(index::AbstractDocumentIndex,
    spectrum::TrainedSpectrum;
    check_index::Bool = true)
```

Scores all documents in the provided `index` based on the `TrainedSpectrum`. 

The score reflects how closely each document aligns with each of the ends of the trained spectrum.  Scores are left-to-right, ie, a score closer to 0 indicates a higher alignment to `spectrum.spectrum[1]` and a score closer to 1 indicates a higher alignment to `spectrum.spectrum[2]`.

# Arguments

  * `index::AbstractDocumentIndex`: The index containing the documents to be scored.
  * `spectrum::TrainedSpectrum`: The trained spectrum model used for scoring.
  * `check_index::Bool` (optional): If `true`, checks for index ID matching between the provided index and the one used in the spectrum training. Defaults to `true`.

# Returns

  * A vector of scores, each corresponding to a document in the index, in the range [0, 1].

# Example

```julia
# Assuming `index` and `spectrum` are predefined
scores = score(index, spectrum)
```

You can show the top 5 highest scoring documents for the spectrum 2:

```julia
index.docs[first(sortperm(scores, rev = true), 5)]

# Use rev=false if you want to see documents closest to spectrum 1 (opposite end)
```

This function is useful for ranking all documents along the chosen `spectrum`.
