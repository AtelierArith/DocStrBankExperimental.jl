Called when done processing an incoming frame. If error_code is non-zero, an error occurred and the payload may not have been completely received. Invoked once per frame on the websocket's event-loop thread.

Return true to proceed normally. If false is returned, the websocket will read no further data and the connection will close.
