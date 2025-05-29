```
train_spectrum(index::AbstractDocumentIndex,
    spectrum::Tuple{String, String};
    num_samples::Int = 100, verbose::Bool = true,
    rewriter_template::Symbol = :StatementRewriter,
    lambda::Real = 1e-5,
    aigenerate_kwargs::NamedTuple = NamedTuple(),
    aiembed_kwargs::NamedTuple = NamedTuple(),)
```

Train a Spectrum, ie, a two-sided axis of polar opposite concepts.

We effectively identify the "directions" in the embedding space that represent the two concepts that you selected as the opposite ends of the spectrum.

Practically, it takes a `num_samples` documents from `index`, rewrites them through the specified lenses (ends of spectrum), then embeds these rewritten documents, and finally trains a logistic regression model to classify the documents according to the spectrum.

See also: `train!`, `train_concept`, `score`

# Arguments

  * `index::AbstractDocumentIndex`: An index containing the documents to be analyzed. This index should have been previously built using `build_index`.
  * `spectrum::Tuple{String, String}`: A pair of strings representing the two lenses through which the documents will be rewritten. For example, ("optimistic", "pessimistic") could be a spectrum.
  * `num_samples::Int` (optional): The number of documents to sample from the index for training. Defaults to 100.
  * `verbose::Bool` (optional): If `true`, prints detailed logs during the process. Defaults to `true`.
  * `rewriter_template::Symbol` (optional): The template used for rewriting statements. Defaults to `:StatementRewriter`.
  * `lambda::Real` (optional): Regularization parameter for the logistic regression. Defaults to 1e-5. Adjust if your cross-validated accuracy is too low.
  * `aigenerate_kwargs::NamedTuple` (optional): Additional arguments for the `aigenerate` function. See `?aigenerate` for more details.
  * `aiembed_kwargs::NamedTuple` (optional): Additional arguments for the `aiembed` function. See `?aiembed` for more details.

# Returns

  * A `TrainedSpectrum` object containing the trained model (`coeffs`), along with other relevant information like the rewritten document (`docs`) and embeddings (`embeddings`).

# Example

```julia
# Assuming `index` is an existing document index
my_spectrum = ("pessimistic", "optimistic")
spectrum = train_spectrum(index, my_spectrum)
```

Show the top 5 highest scoring documents for the spectrum 2 (`spectrum.spectrum[2]` which is "optimistic" in this example):

```julia
scores = score(index, spectrum)
index.docs[first(sortperm(scores, rev = true), 5)]

# Use rev=false to get the highest scoring documents for spectrum 1 (opposite end)
```

You can customize the analysis by passing additional arguments to the AI generation and embedding functions. For example, you can specify the model to use for generation and how many samples to use:

```julia
spectrum = train_spectrum(index,
    ("forward-looking", "dwelling in the past");
    num_samples = 50, aigenerate_kwargs = (; model = "gpt3t"))
```

This function utilizes large language models to rewrite and analyze the text, providing insights based on the specified spectrum. The output includes embeddings and a model capable of projecting new documents onto this spectrum for analysis.

For troubleshooting, you can fit the model manually and inspect the accuracy:

```julia
X = spectrum.embeddings'
# First half is spectrum 1, second half is spectrum 2
y = vcat(-1ones(length(spectrum.source_doc_ids)), ones(length(spectrum.source_doc_ids))) .|>
    Int
accuracy = cross_validate_accuracy(X, y; k = 4, lambda = 1e-8)
```

Or explore the source documents and re-written documents:

```julia
# source documents
index.docs[spectrum.source_doc_ids]

# re-written documents
spectrum.docs
```
