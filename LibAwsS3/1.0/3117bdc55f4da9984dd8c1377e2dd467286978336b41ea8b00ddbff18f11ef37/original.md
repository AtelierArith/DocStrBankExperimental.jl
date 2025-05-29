```
aws_s3_meta_request_pause(meta_request, out_resume_token)
```

Note: pause is currently only supported on upload requests. In order to pause an ongoing upload, call [`aws_s3_meta_request_pause`](@ref)() that will return resume token. Token can be used to query the state of operation at the pausing time. To resume an upload that was paused, supply resume token in the meta request options structure member [`aws_s3_meta_request_options`](@ref).resume_token. The upload can be resumed either from the same client or a different one. Corner cases for resume upload are as follows: - upload is not MPU - fail with AWS_ERROR_UNSUPPORTED_OPERATION - pausing before MPU is created - NULL resume token returned. NULL resume token is equivalent to restarting upload - pausing in the middle of part transfer - return resume token. scheduling of new part uploads stops. - pausing after completeMPU started - return resume token. if s3 cannot find find associated MPU id when resuming with that token and num of parts uploaded equals to total num parts, then operation is a no op. Otherwise operation fails. Note: for no op case the call will succeed and finish/shutdown request callbacks will fire, but on headers callback will not fire. Note: similar to cancel pause does not cancel requests already in flight and and parts might complete after pause is requested.

# Arguments

  * `meta_request`: pointer to the [`aws_s3_meta_request`](@ref) of the upload to be paused
  * `resume_token`: resume token

# Returns

either AWS_OP_ERR or AWS_OP_SUCCESS

### Prototype

```c
int aws_s3_meta_request_pause( struct aws_s3_meta_request *meta_request, struct aws_s3_meta_request_resume_token **out_resume_token);
```
