`DictionaryOperator` represents any linear operator that maps coefficients of a source set to coefficients of a destination set. Typically, source and destination are of type `Dictionary`. The action of the operator is defined by providing a method for apply!.

The dimension of an operator are like a matrix: `(length(dest),length(src))`.

Source and destination should at least implement the following:

  * `length`
  * `size`
  * `eltype`

The element type should be equal for src and dest.
