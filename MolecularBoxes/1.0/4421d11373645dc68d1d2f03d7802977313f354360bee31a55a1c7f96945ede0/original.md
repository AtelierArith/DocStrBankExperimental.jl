MolecularBox has three type parameters:     * V: An immutable vector such as those implemented in the StaticArrays         package     * N: The number of dimensions     * P: A tuple of booleans indicating which dimensions are periodic

Concrete types inheriting from MolecularBox must implement 2 fields: vectors and lengths  si(::Box)
