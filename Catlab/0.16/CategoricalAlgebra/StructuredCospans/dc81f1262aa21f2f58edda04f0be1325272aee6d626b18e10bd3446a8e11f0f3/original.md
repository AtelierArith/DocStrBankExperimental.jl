Structured cospan.

The first type parameter `L` encodes a functor L: A → X from the base category `A`, often FinSet, to a category `X` with "extra structure." An L-structured cospan is then a cospan in X whose feet are images under L of objects in A. The category X is assumed to have pushouts.

Structured cospans form a double category with no further assumptions on the functor L. To obtain a symmetric monoidal double category, L must preserve finite coproducts. In practice, L usually has a right adjoint R: X → A, which implies that L preserves all finite colimits. It also allows structured cospans to be constructed more conveniently from an object x in X plus a cospan in A with apex R(x).

See also: [`StructuredMulticospan`](@ref).
