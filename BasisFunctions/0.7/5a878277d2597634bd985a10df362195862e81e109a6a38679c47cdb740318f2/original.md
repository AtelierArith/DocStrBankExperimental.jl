A `Dictionary{S,T}` is an ordered family of functions, in which each function maps a variable of type `S` to a variable of type `T`. The dictionary can be thought of as an array, where the elements are functions that map `S` to `T`.

A `Dictionary{S,T}` has domain type `S` and codomain type `T`. The domain type corresponds to the type of a domain in the `DomainSets.jl` package, and it is the type of the expected argument to the elements of the dictionary. The codomain type is the type of the output.

Each dictionary is ordered via its index set: the ordering is determined by the iterator of the index set. A dictionary `d` can be indexed in several ways:

  * the linear index is a positive natural number between `1` and `length(d)`
  * the native index is an index that more closely corresponds to the conventional mathematical notation of the dictionary, if that differs from linear indexing. For example, polynomials may have degree ranging from `0` to `length(d)-1`. Fourier series may have negative frequencies.

Some dictionaries define other types of indices, such as multilinear and product indices. See `CompositeDictionary` and `ProductDictionary`. There is always a bijection between the different types of index sets supported by a dictionary.

A dictionary is the basic building block of the package. They can support several operations, such as interpolation, evaluation, differentiation and others. This functionality is made available using a specific interface. See the documentation of the features for a description of that interface and the syntax.
