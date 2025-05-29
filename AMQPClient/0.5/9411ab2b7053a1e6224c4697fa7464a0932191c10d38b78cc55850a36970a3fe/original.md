Cancels a consumer.

This does not affect already delivered messages, but it does mean the server will not send any more messages for that consumer. The client may receive an arbitrary number of  messages in between sending the cancel method and receiving the cancel­ok reply. 
