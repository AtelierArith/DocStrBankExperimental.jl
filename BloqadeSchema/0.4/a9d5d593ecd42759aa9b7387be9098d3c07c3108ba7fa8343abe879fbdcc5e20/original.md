function to*braket*ahs*ir(bloqade*task::BloqadeSchema.QuEraTaskSpecification)

Converts a `bloqade_task` into a `Braket.IR.AHSProgram` capable of being submitted to AWS Braket for execution on a QPU.

NOTE: `BloqadeSchema.QuEraTaskSpecification` contains a field `nshots` which does not have a corresponding field in `Braket.IR.AHSProgram`. This value must be fed as a keyword argument to a `Braket.AwsDevice` instance separately.
