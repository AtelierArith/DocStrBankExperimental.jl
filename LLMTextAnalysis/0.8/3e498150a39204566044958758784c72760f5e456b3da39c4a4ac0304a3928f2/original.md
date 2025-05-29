```
TrainedSpectrum
```

The `TrainedSpectrum` is used to score documents across a spectrum defined by two contrasting concepts. 

It encapsulates the essential information required to evaluate and score documents based on their alignment with the specified spectrum.

Note: `TrainedSpectrum` supports functor behavior, allowing it to be used as a function to score documents in an `AbstractDocumentIndex` based on their alignment with the spectrum.

# Fields

  * `index_id`: A unique identifier for the `AbstractDocumentIndex` associated with the spectrum.
  * `source_doc_ids`: Indices of the documents from the `AbstractDocumentIndex` used for training the spectrum model. Corresponds to `index.docs`.
  * `spectrum`: A tuple containing the two contrasting concepts (as strings) that define the spectrum.
  * `docs`: A collection of rewritten documents, modified to align with the two ends of the spectrum.
  * `embeddings`: The embeddings of the rewritten documents, used for training the model. Columns are documents, rows are dimensions.
  * `coeffs`: Coefficients of the trained logistic regression model, corresponding to each dimension in `embeddings`.

# Example

```julia

index = build_index(...)

# Create and train a spectrum model
spectrum = TrainedSpectrum(index, ("innovation", "tradition"))

# Using TrainedSpectrum for scoring
scores = score(index, concept)
# or use it as a functor: `scores = spectrum(index)`

# Accessing the model details
println("Spectrum: ", spectrum.spectrum)
println("Coefficients: ", spectrum.coeffs)
println("Source Document IDs: ", spectrum.source_doc_ids)
println("Re-written Documents: ", spectrum.docs) # good for debugging if results are poor
```
