Optional callback, for you to review an upload before it completes. For example, you can review each part's checksum and fail the upload if you do not agree with them.

Return AWS_OP_SUCCESS to continue processing the request.

Return aws_raise_error(E) to cancel the request. The error you raise will be reflected in `[`aws*s3*meta*request*result`](@ref).error\_code`. If you're not sure which error to raise, use AWS_ERROR_S3_CANCELED.

WARNING: This feature is experimental/unstable. At this time, the callback is only invoked for multipart upload (when Content-Length is above the `multipart_upload_threshold`, or Content-Length not specified).

# Arguments

  * `meta_request`: pointer to the [`aws_s3_meta_request`](@ref) of the upload.
  * `info`: Detailed info about the upload.
