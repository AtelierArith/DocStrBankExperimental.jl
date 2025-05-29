```
submit_to_braket(h::BloqadeExpr.RydbergHamiltonian, translation_params::BloqadeSchema.SchemaTranslationParams; <keyword arguments>)
```

Submits a `BloqadeExpr.RydbergHamiltonian` instance to Braket with `BloqadeSchema.SchemaTranslationParams` containing the number of shots and  device capabilities. Returns an `AWS.AwsQuantumTask` upon converting the Hamiltonian to one the hardware can execute and submitting it.

Credentials can be passed in explicitly through an `AWS.AWSCredentials` struct or by passing in  `nothing`, in which case credentials will be sought in the standard AWS locations.

# Keyword Arguments

  * `arn="arn:aws:braket:us-east-1::device/qpu/quera/Aquila"`: ARN for the machine
  * `region="us-east-1"`: AWS Region machine is located in
  * `credentials::Union{AWSCredentials, Nothing}=nothing`: `AWS.AWSCredentials` instance you can create to login.

# Logs/Warnings/Exceptions

An `AWS.NoCredentials` exception is thrown containing a `message` string "Can't find AWS credentials!" if the credentials given are invalid.

[`hardware_transform`](@ref) is always invoked internally, meaning its debug logs are also always emitted containing the difference (error) between the original waveforms in `h` and the newly generated ones compatible with hardware as well as the same transformation for atom positions.
