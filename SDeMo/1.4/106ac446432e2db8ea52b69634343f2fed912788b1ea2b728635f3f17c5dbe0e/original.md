```
Logistic
```

Logistic regression with default learning rate of 0.01, penalization (L2) of 0.1, and 2000 epochs. Note that interaction terms can be turned on and off through the use of the `interactions` field. Possible values are `:all` (default), `:self` (only squared terms), and `:none` (no interactions).

The `verbose` field (defaults to `false`) can be used to show the progress of gradient descent, by showing the loss every 100 epochs, or to the value of the `verbosity` field. Note that when doing cross-validation, the loss on the validation data will be automatically reported.
