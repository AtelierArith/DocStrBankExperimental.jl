```
MultinomialNBClassifier
```

A model type for constructing a multinomial naive Bayes classifier, based on [NaiveBayes.jl](https://github.com/dfdx/NaiveBayes.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
MultinomialNBClassifier = @load MultinomialNBClassifier pkg=NaiveBayes
```

Do `model = MultinomialNBClassifier()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `MultinomialNBClassifier(alpha=...)`.

The [multinomial naive Bayes classifier](https://en.wikipedia.org/wiki/Naive_Bayes_classifier#Multinomial_naive_Bayes) is often applied when input features consist of a counts (scitype `Count`) and when observations for a fixed target class are generated from a multinomial distribution with fixed probability vector, but whose sample length varies from observation to observation. For example, features might represent word counts in text documents being classified by sentiment.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype `Count`; check the column scitypes with `schema(X)`.
  * `y` is the target, which can be any `AbstractVector` whose element scitype is `Finite`; check the scitype with `schema(y)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `alpha=1`: Lindstone smoothing in estimation of multinomial probability vectors from training histograms (default corresponds to Laplacian smoothing).

# Operations

  * `predict(mach, Xnew)`: return predictions of the target given new features `Xnew`, which should have the same scitype as `X` above.
  * `predict_mode(mach, Xnew)`: Return the mode of above predictions.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `c_counts`: A dictionary containing the observed count of each input class.
  * `x_counts`: A dictionary containing the categorical counts of each input class.
  * `x_totals`: The sum of each count (input feature), ungrouped.
  * `n_obs`: The total number of observations in the training data.

# Examples

```
using MLJ
import TextAnalysis

CountTransformer = @load CountTransformer pkg=MLJText
MultinomialNBClassifier = @load MultinomialNBClassifier pkg=NaiveBayes

tokenized_docs = TextAnalysis.tokenize.([
    "I am very mad. You never listen.",
    "You seem to be having trouble? Can I help you?",
    "Our boss is mad at me. I hope he dies.",
    "His boss wants to help me. She is nice.",
    "Thank you for your help. It is nice working with you.",
    "Never do that again! I am so mad. ",
])

sentiment = [
    "negative",
    "positive",
    "negative",
    "positive",
    "positive",
    "negative",
]

mach1 = machine(CountTransformer(), tokenized_docs) |> fit!

# matrix of counts:
X = transform(mach1, tokenized_docs)

# to ensure scitype(y) <: AbstractVector{<:OrderedFactor}:
y = coerce(sentiment, OrderedFactor)

classifier = MultinomialNBClassifier()
mach2 = machine(classifier, X, y)
fit!(mach2, rows=1:4)

# probabilistic predictions:
y_prob = predict(mach2, rows=5:6) # distributions
pdf.(y_prob, "positive") # probabilities for "positive"
log_loss(y_prob, y[5:6])

# point predictions:
yhat = mode.(y_prob) # or `predict_mode(mach2, rows=5:6)`
```

See also [`GaussianNBClassifier`](@ref)
