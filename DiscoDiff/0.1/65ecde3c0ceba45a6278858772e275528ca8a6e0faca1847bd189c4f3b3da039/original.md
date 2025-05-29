```
heaviside(Number, [steepnes]) -> Number
```

Implements the Heaviside function in the forward pass.  It is 1 if x > 0 and 0 otherwise. The derivative is taken to be the sigmoid. An extra parameter k controls the  steepnes of the sigmoid, default is 1.
