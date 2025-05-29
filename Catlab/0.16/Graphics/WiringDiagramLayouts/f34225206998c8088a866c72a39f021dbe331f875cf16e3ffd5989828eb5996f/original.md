Backend-agnostic layout of wiring diagrams via morphism expressions.

This module lays out wiring diagrams for visualization, independent of any specific graphics system. It uses the structure of a morphism expression to determine the layout. Thus, the first step of the algorithm is to convert the wiring diagram to a symbolic expression, using the submodule `WiringDiagrams.Expressions`. Morphism expressions may also be given directly.
