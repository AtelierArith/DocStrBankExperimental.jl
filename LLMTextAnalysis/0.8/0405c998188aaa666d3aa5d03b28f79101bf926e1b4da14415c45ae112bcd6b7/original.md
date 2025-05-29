```
(classifier::TrainedClassifier)(
    index::AbstractDocumentIndex; check_index::Bool = true)
```

A method definition that allows a `TrainedClassifier` object to be called as a function to score documents in an `index`. This method delegates to the `score` function.

The score reflects how closely each document aligns to each label in the trained classifier (`classifier.labels`). 

The resulting scores will be a matrix of probabilities for each document and each label.

Scores dimension: `num_documents x num_labels`, ie, position [1,3] would correspond to the probability of the first document corresponding to the 3rd label/class.

To pick the best label for each document, you can use `argmax(scores, dims=2)`.

# Arguments

  * `index::AbstractDocumentIndex`: The index containing the documents to be scored.
  * `return_labels::Bool` (optional): If `true`, returns the most probable labels instead of the scores. Defaults to `false`.
  * `check_index::Bool` (optional): If `true`, performs a check to ensure that the index ID matches the one used in the classifier training. Defaults to `true`.

# Returns

  * A vector of scores in the range [0, 1], each corresponding to a document in the index.

# Example

```julia
# Assuming `index` and `classifier` are predefined
scores = classifier(index)
```

Pick the highest scoring label for each document:

```julia
best_labels = score(index, classifier; return_labels = true)
```

This method provides a convenient and intuitive way to apply a trained classifier model to a document index for scoring.
