Commutative square in a category.

Commutative squares in a category $C$ form the cells of a strict double category, the *arrow double category* or *double category of squares* in $C$, with composition in both directions given by pasting of commutative squares.

In this data structure, the four morphisms comprising the square are stored as a static vector of length 4, ordered as domain (top), codomain (bottom), source (left), and target (right). This convention agrees with the GAT for double categories (`ThDoubleCategory`).
