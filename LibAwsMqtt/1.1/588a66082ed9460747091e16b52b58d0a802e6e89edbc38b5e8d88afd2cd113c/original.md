Called when a connection attempt is completed, either in success or error.

If error code is AWS_ERROR_SUCCESS, then a CONNACK has been received from the server and return_code and session_present contain the values received. If error_code is not AWS_ERROR_SUCCESS, it refers to the internal error that occurred during connection, and return_code and session_present are invalid.
