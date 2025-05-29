Invoked to provide response headers received during execution of the meta request, both for success and error HTTP status codes.

Return AWS_OP_SUCCESS to continue processing the request.

Return aws_raise_error(E) to cancel the request. The error you raise will be reflected in `[`aws*s3*meta*request*result`](@ref).error\_code`. If you're not sure which error to raise, use AWS_ERROR_S3_CANCELED.
