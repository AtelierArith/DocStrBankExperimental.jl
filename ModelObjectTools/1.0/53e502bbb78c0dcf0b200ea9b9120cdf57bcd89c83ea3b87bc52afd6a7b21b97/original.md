vectorRepresentation(input;         fields = fieldnames(typeof(input)))

Creates a vector of real values that represents either model parameters or equilibrium variables. This vector can be used for optimization without the need for constraints; all elements can vary in (-Inf, Inf) while keeping the values within bounds defined  by modelObjectToolsVarInfo.

By default, it will encode all fields of the input structure. If only a subset of fields is desired, then set the fields keyword argument.
