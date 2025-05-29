```
streamed_request!(cb::AbstractStreamCallback, url, headers, input; kwargs...)
```

End-to-end wrapper for POST streaming requests.  In-place modification of the callback object (`cb.chunks`) with the results of the request being returned. We build the `body` of the response object in the end and write it into the `resp.body`.

Returns the response object.

# Arguments

  * `cb`: The callback object.
  * `url`: The URL to send the request to.
  * `headers`: The headers to send with the request.
  * `input`: A buffer with the request body.
  * `kwargs`: Additional keyword arguments.
