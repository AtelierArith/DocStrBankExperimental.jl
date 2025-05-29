Called repeatedly as the websocket's payload is streamed out. The user should write payload data to out_buf, up to available capacity. The websocket will mask this data for you, if necessary. Invoked repeatedly on the websocket's event-loop thread.

Return true to proceed normally. If false is returned, the websocket will send no further data, the frame will complete with an error-code, and the connection will close.
