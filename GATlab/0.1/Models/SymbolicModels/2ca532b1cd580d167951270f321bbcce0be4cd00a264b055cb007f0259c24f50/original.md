Base type for expressions in the syntax of a GAT. This is an alternative to `AlgTerm` used for backwards compatibility with Catlab.

We define Julia types for each *type constructor* in the theory, e.g., object, morphism, and 2-morphism in the theory of 2-categories. Of course, Julia's type system does not support dependent types, so the type parameters are incorporated in the Julia types. (They are stored as extra data in the expression instances.)

The concrete types are structurally similar to the core type `Expr` in Julia. However, the *term constructor* is represented as a type parameter, rather than as a `head` field. This makes dispatch using Julia's type system more convenient.
