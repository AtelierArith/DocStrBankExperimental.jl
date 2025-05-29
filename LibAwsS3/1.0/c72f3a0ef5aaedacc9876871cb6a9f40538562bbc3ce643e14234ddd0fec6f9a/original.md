Invoked to provide the response body as it is received.

Note: If you set `enable_read_backpressure` true on the S3 client, you must maintain the flow-control window. The flow-control window shrinks as you receive body data via this callback. Whenever the flow-control window reaches 0 you will stop downloading data. Use [`aws_s3_meta_request_increment_read_window`](@ref)() to increment the window and keep data flowing. Maintain a larger window to keep up a high download throughput, parts cannot download in parallel unless the window is large enough to hold multiple parts. Maintain a smaller window to limit the amount of data buffered in memory.

If `manual_window_management` is false, you do not need to maintain the flow-control window. No back-pressure is applied and data arrives as fast as possible.

Return AWS_OP_SUCCESS to continue processing the request.

Return aws_raise_error(E) to cancel the request. The error you raise will be reflected in `[`aws*s3*meta*request*result`](@ref).error\_code`. If you're not sure which error to raise, use AWS_ERROR_S3_CANCELED.
