Callback to invoke when the defender task needs to "publish" a report. Useful to override default MQTT publish behavior, for testing report outputs

Notes: * This function should not perform blocking IO. * This function should copy the report if it needs to hold on to the memory for an IO operation

returns: AWS_OP_SUCCESS if the user callback wants to consider the publish failed.
