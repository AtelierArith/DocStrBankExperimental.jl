```
score(index::AbstractDocumentIndex, concept::TrainedConcept; check_index::Bool = true)
```

Scores all documents in the provided `index` based on the `TrainedConcept`. 

The score quantifies the relevance or alignment of each document with the trained concept, with a score closer to 1 indicating a higher relevance.

The function uses a sigmoid function to map the scores to a range between 0 and 1, providing a probability-like interpretation.

# Arguments

  * `index::AbstractDocumentIndex`: The index containing the documents to be scored.
  * `concept::TrainedConcept`: The trained concept model used for scoring.
  * `check_index::Bool` (optional): If `true`, checks for index ID matching between the provided index and the one used in the concept training. Defaults to `true`.

# Returns

  * A vector of scores, each corresponding to a document in the index, in the range [0, 1].

# Example

```julia
# Assuming `index` and `concept` are predefined
scores = score(index, concept)
```

You can show the top 5 highest scoring documents for the concept:

```julia
index.docs[first(sortperm(scores, rev = true), 5)]
```

This function is particularly useful for analyzing the presence, intensity, or relevance of a specific concept within a collection of documents.
