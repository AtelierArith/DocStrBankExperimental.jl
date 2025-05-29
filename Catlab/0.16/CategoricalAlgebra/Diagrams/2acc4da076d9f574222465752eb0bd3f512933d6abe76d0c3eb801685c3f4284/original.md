Morphism of diagrams in a category.

In fact, this type encompasses several different kinds of morphisms from a diagram $D: J → C$ to another diagram $D′: J′ → C$:

1. `DiagramHom{id}`: a functor $F: J → J′$ together with a natural transformation $ϕ: D ⇒ F⋅D′$
2. `DiagramHom{op}`: a functor $F: J′ → J$ together with a natural transformation $ϕ: F⋅D ⇒ D′$
3. `DiagramHom{co}`: a functor $F: J → J′$ together with a natural transformation $ϕ: F⋅D′ ⇒ D$.

Note that `Diagram{op}` is *not* the opposite category of `Diagram{id}`, but `Diagram{op}` and `Diagram{co}` are opposites of each other. Explicit support is included for both because they are useful for different purposes: morphisms of type `DiagramHom{id}` and `DiagramHom{op}` induce morphisms between colimits and between limits of the diagrams, respectively, whereas morphisms of type `DiagramHom{co}` generalize morphisms of polynomial functors.
