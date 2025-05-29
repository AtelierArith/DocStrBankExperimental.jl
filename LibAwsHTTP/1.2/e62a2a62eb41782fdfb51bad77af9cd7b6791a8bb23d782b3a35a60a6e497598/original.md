Invoked when request/response stream destroy completely. This can be invoked within the same thead who release the refcount on http stream. This is invoked even if the stream is never activated.
