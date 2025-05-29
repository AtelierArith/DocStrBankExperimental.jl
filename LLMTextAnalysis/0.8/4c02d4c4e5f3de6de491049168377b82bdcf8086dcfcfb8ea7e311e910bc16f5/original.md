```
TrainedConcept
```

The `TrainedConcept` struct is used for representing and working with a trained concept model.

It encapsulates all the necessary information required to analyze and score documents based on their relevance to a specific concept.

# Fields

  * `index_id`: A unique identifier for the `AbstractDocumentIndex` associated with this concept.
  * `source_doc_ids`: Indices of the documents from the `AbstractDocumentIndex` used for training the concept model. Corresponds to `index.docs`
  * `concept`: The specific concept (as a string) that this model is trained to analyze.
  * `docs`: The collection of rewritten documents, which are modified to reflect the concept.
  * `embeddings`: The embeddings of the rewritten documents, used for training the model. Columns are documents, rows are dimensions.
  * `coeffs`: The coefficients of the trained logistic regression model. Maps to each dimension in `embeddings`.

# Example

```julia
index = build_index(...)

# Training a concept
concept = train_concept(index, "sustainability")

# Using TrainedConcept for scoring
scores = score(index, concept)
# or use it as a functor: `scores = concept(index)`

# Accessing the model details
println("Concept: ", concept.concept)
println("Coefficients: ", concept.coeffs)
println("Source Document IDs: ", concept.source_doc_ids)
println("Re-written Documents: ", concept.docs) # good for debugging if results are poor
```
