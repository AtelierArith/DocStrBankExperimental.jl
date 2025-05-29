```
EntityEmbedder(; model=mljflux_neural_model)
```

`EntityEmbedder` implements entity embeddings as in the "Entity Embeddings of Categorical Variables" paper by Cheng Guo, Felix Berkhahn.

# Training data

In MLJ (or MLJBase) bind an instance unsupervised `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features supported by the model being wrapped. Features to be transformed must  have element scitype `Multiclass` or `OrderedFactor`. Use `schema(X)` to   check scitypes.
  * `y` is the target, which can be any `AbstractVector` supported by the model being wrapped.

Train the machine using `fit!(mach)`.

# Hyper-parameters

  * `model`: The supervised MLJFlux neural network model to be used for entity embedding.  This must be one of these: `MLJFlux.NeuralNetworkClassifier`, `NeuralNetworkBinaryClassifier`, `MLJFlux.NeuralNetworkRegressor`,`MLJFlux.MultitargetNeuralNetworkRegressor`. The selected model may have hyperparameters  that may affect embedding performance, the most notable of which could be the `builder` argument.

# Operations

  * `transform(mach, Xnew)`: Transform the categorical features of `Xnew` into dense `Continuous` vectors using the trained `MLJFlux.EntityEmbedderLayer` layer present in the network.   Check relevant documentation [here](https://fluxml.ai/MLJFlux.jl/dev/) and in particular, the `embedding_dims` hyperparameter.

# Examples

```julia
using MLJ
using CategoricalArrays

# Setup some data
N = 200
X = (;
    Column1 = repeat(Float32[1.0, 2.0, 3.0, 4.0, 5.0], Int(N / 5)),
    Column2 = categorical(repeat(['a', 'b', 'c', 'd', 'e'], Int(N / 5))),
    Column3 = categorical(repeat(["b", "c", "d", "f", "f"], Int(N / 5)), ordered = true),
    Column4 = repeat(Float32[1.0, 2.0, 3.0, 4.0, 5.0], Int(N / 5)),
    Column5 = randn(Float32, N),
    Column6 = categorical(
        repeat(["group1", "group1", "group2", "group2", "group3"], Int(N / 5)),
    ),
)
y = categorical([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])           # Classification

# Initiate model
EntityEmbedder = @load EntityEmbedder pkg=MLJFlux
NeuralNetworkClassifier = @load NeuralNetworkClassifier pkg=MLJFlux

clf = NeuralNetworkClassifier(embedding_dims=Dict(:Column2 => 2, :Column3 => 2))

emb = EntityEmbedder(clf)

# Construct machine
mach = machine(emb, X, y)

# Train model
fit!(mach)

# Transform data using model to encode categorical columns
Xnew = transform(mach, X)
Xnew
```

See also [`NeuralNetworkClassifier`, `NeuralNetworkRegressor`](@ref)
