```
DocStrings
```

Extends Julia `DocStringExtensions` package to provide PALEO-specific "Abbreviations" to list  Reaction Parameters and Variables in docstrings.

exports PARS, METHODS*SETUP, METHODS*INITIALIZE, METHODS_DO

`$(PARS)` expands to a list of Reaction Parameters `$(METHODS_SETUP)`, `$(METHODS_INITIALIZE)`, `$(METHODS_DO)` expand to a list of ReactionMethods and Variables

NB: a Reaction is created with `create_reaction`.  In addition, `$(METHODS_DO)` etc call `register_methods(rj::AbstractReaction)`, so may fail if this call fails with default parameters.
