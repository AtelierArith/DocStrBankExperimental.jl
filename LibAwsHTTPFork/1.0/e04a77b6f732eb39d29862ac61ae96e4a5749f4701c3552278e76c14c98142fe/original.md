Called when a new frame arrives. Invoked once per frame on the websocket's event-loop thread. Each incoming-frame-begin call will eventually be followed by an incoming-frame-complete call, before the next frame begins and before the websocket shuts down.

Return true to proceed normally. If false is returned, the websocket will read no further data, the frame will complete with an error-code, and the connection will close.
