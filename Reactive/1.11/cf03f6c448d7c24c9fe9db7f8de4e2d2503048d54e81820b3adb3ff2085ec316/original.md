```
flatten(input::Signal{Signal}; typ=Any)
```

Flatten a signal of signals into a signal which holds the value of the current signal. The `typ` keyword argument specifies the type of the flattened signal. It is `Any` by default.
