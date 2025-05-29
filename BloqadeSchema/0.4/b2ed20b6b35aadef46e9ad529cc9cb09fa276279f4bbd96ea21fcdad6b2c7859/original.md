```
sumbit_to_braket(ts:BloqadeSchema.QuEraTaskSpecification; <keyword arguments>)
```

Submits a `BloqadeSchema.QuEraTaskSpecification` instance to Braket, returning an `AWS.AwsQuantumTask`.

Credentials can be passed in explicitly through an `AWS.AWSCredentials` struct or by passing in  `nothing`, in which case credentials will be sought in the standard AWS locations.

# Keyword Arguments

  * `arn="arn:aws:braket:us-east-1::device/qpu/quera/Aquila"`: ARN for the machine
  * `region="us-east-1"`: AWS Region machine is located in
  * `credentials::Union{AWSCredentials, Nothing}=nothing`: `AWS.AWSCredentials` instance you can create to login.

# Logs/Warnings/Exceptions

An `AWS.NoCredentials` exception is thrown containing a `message` string "Can't find AWS credentials!" if the credentials given are invalid.
