```
(p::ProjectTo{T})(dx)
```

Projects the tangent `dx` onto a specific tangent space.

The type `T` is meant to encode the largest acceptable space, so usually this enforces `p(dx)::T`. But some subspaces which aren't subtypes of `T` may be allowed, and in particular `dx::AbstractZero` always passes through.

Usually `T` is the "outermost" part of the type, and `p` stores additional properties such as projectors for each constituent field. Arrays have either one projector `p.element` expressing the element type for an array of numbers, or else an array of projectors `p.elements`. These properties can be supplied as keyword arguments on construction, `p = ProjectTo{T}(; field=data, element=Projector(x))`. For each `T` in use, corresponding methods should be written for `ProjectTo{T}(dx)` with nonzero `dx`.

When called on `dx::Thunk`, the projection is inserted into the thunk.
