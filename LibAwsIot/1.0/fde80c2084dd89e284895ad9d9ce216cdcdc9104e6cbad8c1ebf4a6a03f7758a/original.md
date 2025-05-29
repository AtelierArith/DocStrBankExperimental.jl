User callback type invoked to retrieve a string list custom metric

List provided will already be initialized and caller must push items into the list of type (`struct aws_string *`). String allocated that are placed into the list are destroyed by the defender task after it is done with the list.

returns: AWS_OP_SUCCESS if the custom metric was successfully added to the task config
