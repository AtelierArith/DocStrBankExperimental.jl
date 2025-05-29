`LengthRange(zeroth, step, length)`

A LengthRange is a range which allows (but does not require) its `zeroth`, `step` and/or `length` to be `Static` numbers.

The `zeroth` element of the range is the element before the first. Although it is not part of the range, it is frequently useful for it to remain static. For example, if the common 1:n range is multiplied by a scalar, the zeroth element can remain `StaticInteger{0}`

The `step` is the distance between successive elements of the range.

The `length` must be an `Integer`. A `LengthRange` is parameterized by its length, rather than its last element. This makes it possible for the length to remain `Static` when an offset is added to the range.

`LengthRange` is the union of `LengthStepRange` and `LengthUnitRange` which are subtypes of `OrdinalRange` and `AbstractUnitRange` respectively.
