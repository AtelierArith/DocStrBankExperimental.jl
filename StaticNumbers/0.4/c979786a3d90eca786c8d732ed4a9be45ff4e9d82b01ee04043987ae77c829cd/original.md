A `LengthUnitRange` is a type that is identical to `LengthStepRange` but where the step is fixed to 1. It is a subtype of UnitRange.

(It would be much simpler to just use `LengthStepRange` with a `Static` step of 1 but then methods that expect a `UnitRange` would not work.)
