checkValidity(m)

Checks that either parameters or endogenous variables lie within  bounds and satisfy other normalizations/constraints embedded in the modelObjectToolsVarInfo dictionary. Every component of the structure m must be a  variable registered in the modelObjectToolsVarInfo dictionary, using the addVarInfo() function.

Returns a tuple where the first element is a boolean indicating validity, the second element is either nothing or a symbol indicating the invalid parameter, and the third element is either nothing or the invalid value.
