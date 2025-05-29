Abstract base class for all specialized bases.

The Basis class is meant to specify a basis of the Hilbert space of the studied system. Besides basis specific information all subclasses must implement a shape variable which indicates the dimension of the used Hilbert space. For a spin-1/2 Hilbert space this would be the vector `[2]`. A system composed of two spins would then have a shape vector `[2 2]`.

Composite systems can be defined with help of the [`CompositeBasis`](@ref) class.
