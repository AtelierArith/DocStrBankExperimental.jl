A `MultiDict` is the concatenation of several dictionaries. The components are contained in an indexable set, such as a tuple or an array. In case of an array, the number of dictionaries may be large.

The native representation of a `MultiDict` is a `BlockVector`, of which each element is the native representation of the corresponding element of the multidict.

Evaluation of an expansion at a point is defined by summing the evaluation of all functions in the set at that point.
