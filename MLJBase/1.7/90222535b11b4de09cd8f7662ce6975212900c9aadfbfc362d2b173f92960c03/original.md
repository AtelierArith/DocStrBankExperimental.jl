```
default_logger(logger)
```

Reset the default logger.

# Example

Suppose an [MLflow](https://mlflow.org/docs/latest/index.html) tracking service is running on a local server at `http://127.0.0.1:500`. Then in every `evaluate` call in which `logger` is not specified, the peformance evaluation is automatically logged to the service, as here:

```julia
using MLJ
logger = MLJFlow.Logger("http://127.0.0.1:5000/api")
default_logger(logger)

X, y = make_moons()
model = ConstantClassifier()
evaluate(model, X, y, measures=[log_loss, accuracy)])
```
