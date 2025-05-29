```
train_classifier(index::AbstractDocumentIndex,
    labels::AbstractVector{<:AbstractString};
    docs_ids::AbstractVector{<:Integer} = Int[],
    docs_labels::AbstractVector{<:Integer} = Int[],
    labels_description::Union{Nothing, AbstractVector{<:AbstractString}} = nothing,
    num_samples::Int = 5, verbose::Bool = true,
    writer_template::Symbol = :TextWriterFromLabel,
    lambda::Real = 1e-3,
    aigenerate_kwargs::NamedTuple = NamedTuple(),
    aiembed_kwargs::NamedTuple = NamedTuple())
```

Train a model to classify each document into one of several specific topics based on `labels` (detailed in `labels_description`).

If user provides documents from the index and their corresponding labels (`docs_ids` and `docs_labels`, respectively),  the model will be trained on those documents. Aim for a balanced dataset (all `labels` must be present) and a minimum of 5 documents per label (ideally more).

Otherwise, we will first generate `num_samples` of synthetic documents for each label in `labels`, ie, in total there will be `num_samples x length(labels)` generated documents. If `labels_description` is provided, these descriptions will be provided to the AI model to generate more diverse and relevant documents for each label (more informative than just one word labels).

Under the hood, we train a multi-label classifier on top of the embeddings of the documents.

The resulting scores will be a matrix of probabilities for each document and each label. Scores dimension: `num_documents x num_labels`, ie, position [1,3] would correspond to the probability of the first document corresponding to the 3rd label/class. To pick the best label for each document, you can use `argmax(scores, dims=2)`.

See also: `score`, `train!`, `train_spectrum`, `train_concept`

# Arguments

  * `index::AbstractDocumentIndex`: An index containing the documents to be analyzed.
  * `labels::AbstractVector{<:AbstractString}`: A vector of labels to be used for training the classifier (documents will be assigned to one of these labels).
  * `docs_ids::AbstractVector{<:Integer}` (optional): The IDs of the documents in the `index` to be used for training. Defaults to an empty vector and will generate synthetic documents.
  * `docs_labels::AbstractVector{<:Integer}` (optional): The labels corresponding to the documents in `docs_ids`. Defaults to an empty vector.
  * `labels_description::Union{Nothing, AbstractVector{<:AbstractString}}` (optional): A vector of descriptions for each label. If provided, it will be used to generate more diverse and relevant documents for each label. Defaults to `nothing`.
  * `num_samples::Int` (optional): The number of documents to generate for each label in `labels`. Defaults to 5.
  * `verbose::Bool` (optional): If `true`, prints detailed logs during the process. Defaults to `true`.
  * `writer_template::Symbol` (optional): The template used for writing synthetic documents. Defaults to `:TextWriterFromLabel`.
  * `lambda::Real` (optional): Regularization parameter for logistic regression. Defaults to 1e-3
  * `aigenerate_kwargs::NamedTuple` (optional): Additional arguments for the `aigenerate` function. See `?aigenerate` for more details.
  * `aiembed_kwargs::NamedTuple` (optional): Additional arguments for the `aiembed` function. See `?aiembed` for more details.

# Returns

  * A `TrainedClassifier` object containing the trained model, along with relevant information such as the generated documents (`docs`), embeddings (`embeddings`), and model coefficients (`coeffs`).

# Example

Create a classifier for a set of labeled documents in our index (ie, we know the labels for some documents):

```julia
# Assuming `index` is an existing document index

# Provide the names of the topics and corresponding labeled documents
labels = ["Improving traffic situation", "Taxes and public funding",
    "Safety and community", "Other"]

# Let's say we have labeled a few documents - ideally, you should have 5-10 examples for EACH label
docs_ids = [1, 2674, 4, 17, 23, 69, 2669, 6]
docs_labels = [1, 1, 2, 2, 3, 3, 4, 4] # what topic each doc belongs to

# Train the classifier
cls = train_classifier(index, labels; docs_ids, docs_labels)

# Score the documents in the index
score(index, cls) # or cls(index)
```

If you do not have any labeled documents, you can ask an AI model to generate some potential examples for you (`num_samples` per each topic/label). It helps to provide label descriptions to improve the quality of generated documents:

```julia
# Assuming `index` is an existing document index

labels_description = [
    "Survey responses around infrastructure, improving traffic situation and related",
    "Decreasing taxes and giving more money to the community",
    "Survey responses around Homelessness, general safety and community related topics",
    "Any other topics like environment, education, governance, etc."]

# Train the classifier - it will generate 20 document examples (5 for each label x 4 labels)
cls = train_classifier(index, labels; labels_description, num_samples=5)

# Get scores for all documents
scores = score(index, cls)

# Get labels for all documens in the index
best_labels = score(index, cls; return_labels = true)
```
