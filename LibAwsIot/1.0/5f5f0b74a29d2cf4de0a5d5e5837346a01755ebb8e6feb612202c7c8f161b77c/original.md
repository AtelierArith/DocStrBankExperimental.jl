User callback type invoked when a report fails to submit.

There are two possibilities for failed submission: 1. The MQTT client fails to publish the message and returns an error code. In this scenario, the client_error_code will be a value other than AWS_ERROR_SUCCESS. The rejected_message_payload parameter will be NULL. 2. After a successful publish, a reply is received on the respective MQTT rejected topic with a message. In this scenario, the client_error_code will be AWS_ERROR_SUCCESS, and rejected_message_payload will contain the payload of the rejected message received.

# Arguments

  * `rejected_message_payload`:[in] response payload recieved from rejection topic
  * `userdata`:[in] callback userdata
