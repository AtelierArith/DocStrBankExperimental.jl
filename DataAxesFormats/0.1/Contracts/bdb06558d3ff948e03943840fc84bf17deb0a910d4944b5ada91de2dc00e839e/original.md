The expectation from a specific property for a computation on `Daf` data.

Input data:

`RequiredInput` - data that must exist in the data when invoking the computation, will be used as input.

`OptionalInput` - data that, if existing in the data when invoking the computation, will be used as an input.

Output data:

`GuaranteedOutput` - data that is guaranteed to exist when the computation is done.

`OptionalOutput` - data that may exist when the computation is done, depending on some condition, which may include the existence of optional input and/or the value of parameters to the computation, and/or the content of the data.
