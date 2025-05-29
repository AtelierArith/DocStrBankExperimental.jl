```
manipulate(f::Function; parameters, config=())
```

Create an interactive plot updated by callback `f`. Only works in Jupyter Notebook.

# Arguments

  * `f::Function`: callback for generating a plot; interactively updated configuration `c` is provided.
  * `parameters`: parameters adjustable with interactive widgets; value should be an iterable.
  * `config=()`: a baseline configuration.
