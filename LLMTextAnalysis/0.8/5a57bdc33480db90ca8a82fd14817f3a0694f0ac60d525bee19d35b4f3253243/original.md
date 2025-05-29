```
score(index::AbstractDocumentIndex,
    classifier::TrainedClassifier;
    check_index::Bool = true)
```

Scores all documents in the provided `index` based on the `TrainedClassifier`. 

The score reflects how closely each document aligns to each label in the trained classifier (`classifier.labels`). 

The resulting scores will be a matrix of probabilities for each document and each label.

Scores dimension: `num_documents x num_labels`, ie, position [1,3] would correspond to the probability of the first document corresponding to the 3rd label/class.

To pick the best label for each document, you can use `argmax(scores, dims=2)`.

# Arguments

  * `index::AbstractDocumentIndex`: The index containing the documents to be scored.
  * `classifier::TrainedClassifier`: The trained classifier model used for scoring.
  * `return_labels::Bool` (optional): If `true`, returns the most probable labels instead of the scores. Defaults to `false`.
  * `check_index::Bool` (optional): If `true`, checks for index ID matching between the provided index and the one used in the classifier training. Defaults to `true`.

# Returns

  * A matrix of scores, each row corresponding to a document in the index and each column corresponding to probability of that label.

# Example

```julia
# Assuming `index` and `classifier` are predefined
scores = score(index, classifier)
```

Pick the highest scoring label for each document:

```julia
scores = score(index, classifier)
label_ids = argmax(scores, dims = 2) |> vec |> x -> map(i -> i[2], x)
best_labels = classifier.labels[label_ids]
```

Or, instead, you can simply provide `return_labels=true` to get the best labels directly:

```julia
score(index, classifier; return_labels = true)
```
