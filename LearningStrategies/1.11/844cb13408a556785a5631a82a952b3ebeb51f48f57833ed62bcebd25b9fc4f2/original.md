```
Verbose(s::LearningStrategy)
Verbose(s::LearningStrategy, io::IO)
```

Allow the LearningStrategy `s` to print output.

  * Will automatically print when `finished(s, args...) == true`.
  * Other methods should be overloaded to add printout.

      * For example: `update!(model, v::Verbose{MyStrategy}, item) = ...`
