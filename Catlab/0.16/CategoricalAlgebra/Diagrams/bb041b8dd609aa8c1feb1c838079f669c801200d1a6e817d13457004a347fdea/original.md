Diagram in a category.

Recall that a *diagram* in a category $C$ is a functor $D: J → C$, where for us the *shape category* $J$ is finitely presented. Although such a diagram is captured perfectly well by a `FinDomFunctor`, there are several different notions of morphism between diagrams. The first type parameter `T` in this wrapper type distinguishes which diagram category the diagram belongs to. See [`DiagramHom`](@ref) for more about the possible choices. The parameter `T` may also be `Any` to indicate that no choice has (yet) been made.
