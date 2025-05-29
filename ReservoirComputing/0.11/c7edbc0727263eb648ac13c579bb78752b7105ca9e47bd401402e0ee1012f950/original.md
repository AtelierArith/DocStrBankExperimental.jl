```
Generative(prediction_len)
```

A prediction strategy that enables models to generate autonomous multi-step forecasts by recursively feeding their own outputs back as inputs for subsequent prediction steps.

# Parameters

  * `prediction_len`: The number of future steps to predict.

# Description

The `Generative` prediction method allows a model to perform multi-step forecasting by using its own previous predictions as inputs for future predictions.

At each step, the model takes the current input, generates a prediction, and then incorporates that prediction into the input for the next step. This recursive process continues until the specified number of prediction steps (`prediction_len`) is reached.
