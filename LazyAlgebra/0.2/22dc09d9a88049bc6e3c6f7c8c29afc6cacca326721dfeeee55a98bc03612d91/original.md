A `Mapping` is any function between two variables spaces. Assuming upper case Latin letters denote mappings, lower case Latin letters denote variables, and Greek letters denote scalars, then:

  * `A*x` or `A⋅x` yields the result of applying the mapping `A` to `x`;
  * `A\x` yields the result of applying the inverse of `A` to `x`;

Simple constructions are allowed for any kind of mappings and can be used to create new instances of mappings which behave correctly. For instance:

  * `B = α*A` (where `α` is a real) is a mapping which behaves as `A` times `α`; that is `B⋅x` yields the same result as `α*(A⋅x)`.
  * `C = A + B + ...` is a mapping which behaves as the sum of the mappings `A`, `B`, ...; that is `C⋅x` yields the same result as `A⋅x + B⋅x + ...`.
  * `C = A*B` or `C = A⋅B` is a mapping which behaves as the composition of the mappings `A` and `B`; that is `C⋅x` yields the same result as `A⋅(B.x)`. As for the sum of mappings, there may be an arbitrary number of mappings in a composition; for example, if `D = A*B*C` then `D⋅x` yields the same result as `A⋅(B⋅(C⋅x))`.
  * `C = A\B` is a mapping such that `C⋅x` yields the same result as `A\(B⋅x)`.
  * `C = A/B` is a mapping such that `C⋅x` yields the same result as `A⋅(B\x)`.

These constructions can be combined to build up more complex mappings. For example:

  * `D = A*(B + C)` is a mapping such that `C⋅x` yields the same result as `A⋅(B⋅x + C⋅x)`.

A `LinearMapping` is any linear mapping between two spaces. This abstract subtype of `Mapping` is introduced to extend the notion of *matrices* and *vectors*. Assuming the type of `A` inherits from `LinearMapping`, then:

  * `A'⋅x` and `A'*x` yields the result of applying the adjoint of the mapping `A` to `x`;
  * `A'\x` yields the result of applying the adjoint of the inverse of mapping `A` to `x`.
  * `B = A'` is a mapping such that `B⋅x` yields the same result as `A'⋅x`.

The following methods should be implemented for a mapping `A` of specific type `M <: Mapping`:

```julia
vcreate(::Type{P}, A::M, x, scratch::Bool) -> y
apply!(α::Number, ::Type{P}, A::M, x, , scratch::Bool, β::Number, y) -> y
```

for any supported operation `P ∈ Operations` (`Direct`, `Adjoint`, `Inverse` and/or `InverseAdjoint`). See the documentation of these methods for explanations. Optionally, methods `P(A)` may be extended, *e.g.* to throw exceptions if operation `P` is forbidden (or not implemented). By default, all these operations are assumed possible (except `Adjoint` and `InverseAdjoint` for a nonlinear mapping).

See also: [`apply`](@ref), [`apply!`](@ref), [`vcreate`](@ref),           [`LinearType`](@ref), [`Scalar`](@ref), [`Direct`](@ref),           [`Adjoint`](@ref), [`Inverse`](@ref), [`InverseAdjoint`](@ref).
