```
GaussianNBClassifier
```

A model type for constructing a Gaussian naive Bayes classifier, based on [NaiveBayes.jl](https://github.com/dfdx/NaiveBayes.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
GaussianNBClassifier = @load GaussianNBClassifier pkg=NaiveBayes
```

Do `model = GaussianNBClassifier()` to construct an instance with default hyper-parameters. 

Given each class taken on by the target variable `y`, it is supposed that the conditional probability distribution for the input variables `X` is a multivariate Gaussian. The mean and covariance of these Gaussian distributions are estimated using maximum likelihood, and a probability distribution for `y` given `X` is deduced by applying Bayes' rule. The required marginal for `y` is estimated using class frequency in the training data.

**Important.** The name "naive Bayes classifier" is perhaps misleading. Since we are learning the full multivariate Gaussian distributions for `X` given `y`, we are not applying the usual naive Bayes independence condition, which would amount to forcing the covariance matrix to be diagonal.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype `Continuous`; check the column scitypes with `schema(X)`
  * `y` is the target, which can be any `AbstractVector` whose element scitype is `Finite`; check the scitype with `schema(y)`

Train the machine using `fit!(mach, rows=...)`.

# Operations

  * `predict(mach, Xnew)`: return predictions of the target given new features `Xnew`, which should have the same scitype as `X` above. Predictions are probabilistic.
  * `predict_mode(mach, Xnew)`: Return the mode of above predictions.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `c_counts`: A dictionary containing the observed count of each input class.
  * `c_stats`: A dictionary containing observed statistics on each input class. Each class is represented by a `DataStats` object, with the following fields:

      * `n_vars`: The number of variables used to describe the class's behavior.
      * `n_obs`: The number of times the class is observed.
      * `obs_axis`: The axis along which the observations were computed.
  * `gaussians`: A per class dictionary of Gaussians, each representing the distribution of the class. Represented with type `Distributions.MvNormal` from the Distributions.jl package.
  * `n_obs`: The total number of observations in the training data.

# Examples

```
using MLJ
GaussianNB = @load GaussianNBClassifier pkg=NaiveBayes

X, y = @load_iris
clf = GaussianNB()
mach = machine(clf, X, y) |> fit!

fitted_params(mach)

preds = predict(mach, X) # probabilistic predictions
preds[1]
predict_mode(mach, X) # point predictions
```

See also [`MultinomialNBClassifier`](@ref)
