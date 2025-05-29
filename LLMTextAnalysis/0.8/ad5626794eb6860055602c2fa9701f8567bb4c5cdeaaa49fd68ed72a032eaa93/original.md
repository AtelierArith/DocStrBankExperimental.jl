```
(concept::TrainedConcept)(index::AbstractDocumentIndex; check_index::Bool = true)
```

A method definition that allows a `TrainedConcept` object to be called as a function to score documents in an `index`. This method delegates to the `score` function.

# Arguments

  * `index::AbstractDocumentIndex`: The index containing the documents to be scored.
  * `check_index::Bool` (optional): If `true`, performs a check to ensure that the index ID matches the one used in the concept training. Defaults to `true`.

# Returns

  * A vector of scores in the range [0, 1], each corresponding to a document in the index.

# Example

```julia
# Assuming `index` and `concept` are predefined
scores = concept(index)
```

This method provides a convenient and intuitive way to apply a trained concept model to a document index for scoring, facilitating thematic analysis and concept relevance studies.
