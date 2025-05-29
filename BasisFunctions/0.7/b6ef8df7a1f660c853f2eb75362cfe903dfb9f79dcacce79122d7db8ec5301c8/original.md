A `DerivedDict` is a dictionary that inherits most of its behaviour from an underlying dictionary.

The abstract type for derived dictionaries implements the interface of a dictionary using composition and delegation. Concrete derived dictionaries may override functions to specialize behaviour. For example, a mapped dictionary may override the evaluation routine to apply the map first.
