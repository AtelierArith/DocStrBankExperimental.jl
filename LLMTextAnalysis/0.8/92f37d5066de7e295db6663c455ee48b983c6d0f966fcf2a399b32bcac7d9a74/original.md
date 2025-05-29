```
train_concept(index::AbstractDocumentIndex,
              concept::String;
              num_samples::Int = 100, verbose::Bool = true,
              rewriter_template::Symbol = :StatementRewriter,
              lambda::Real = 1e-3, negatives_samples::Int = 1,
              aigenerate_kwargs::NamedTuple = NamedTuple(),
              aiembed_kwargs::NamedTuple = NamedTuple(),)
```

Train a model to identify and score a specific Concept (defined by the string `concept`) based on `num_samples documents from`index`.

We effectively identify the "direction" in the embedding space that represent this concept and develop a model to be able to score our documents against it.

This function focuses on a single Concept, as opposed to a Spectrum (see `train_spectrum`), to gauge its presence, strength, or manifestations in the documents.

See also: `train_spectrum`, `train!`, `score`

# Arguments

  * `index::AbstractDocumentIndex`: An index containing the documents to be analyzed.
  * `concept::String`: The concept to be analyzed within the documents.
  * `num_samples::Int` (optional): The number of documents to sample from the index for training. Defaults to 100.
  * `verbose::Bool` (optional): If `true`, prints detailed logs during the process. Defaults to `true`.
  * `rewriter_template::Symbol` (optional): The template used for rewriting statements. Defaults to `:StatementRewriter`.
  * `lambda::Real` (optional): Regularization parameter for logistic regression. Defaults to 1e-3
  * `negatives_samples::Int` (optional): The number of negative examples to use for training per each positive sample. Defaults to 1.
  * `aigenerate_kwargs::NamedTuple` (optional): Additional arguments for the `aigenerate` function. See `?aigenerate` for more details.
  * `aiembed_kwargs::NamedTuple` (optional): Additional arguments for the `aiembed` function. See `?aiembed` for more details.

# Returns

  * A `TrainedConcept` object containing the trained model, along with relevant information such as rewritten documents (`docs`), embeddings (`embeddings`), and model coefficients (`coeffs`).

# Example

```julia
# Assuming `index` is an existing document index
my_concept = "sustainability"
concept_model = train_concept(index, my_concept)
```

Show the top 5 highest scoring documents for the concept:

```julia
scores = score(index, concept)
index.docs[first(sortperm(scores, rev = true), 5)]
```

You can customize the training by passing additional arguments to the AI generation and embedding functions. For example, you can specify the model to use for generation and how many samples to use:

```julia
concept = train_concept(index,
    "action-oriented";
    num_samples = 50,
    aigenerate_kwargs = (; model = "gpt3t"))
```

This function leverages large language models to extract and analyze the presence and variations of a specific concept within a document corpus. It can be particularly useful in thematic studies, sentiment analysis, or trend identification in large collections of text.

For further analysis, you can inspect the rewritten documents and their embeddings:

```julia
# Concept-related rewritten documents
concept_model.docs

# Embeddings of the rewritten documents
concept_model.embeddings
```
