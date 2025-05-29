`@taylorize expr`

This macro `eval`s the function given by `expr` and defines a new method of [`jetcoeffs!`](@ref) which is specialized on that function. Integrating via [`taylorinteg`](@ref) of [`lyap_taylorinteg`](@ref) after using the macro yields better performance.

See the [documentation](@ref taylorize) for more details and limitations.

!!! warning
    This macro is on an experimental stage; check the integration results carefully.

