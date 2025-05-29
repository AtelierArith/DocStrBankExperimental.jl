```
wait_for_event(conn:: XCBConnection) -> (XCBEvent, Bool)
```

Block until an event arrives from the server. Returns the event and whether it was sent using the SendEvent request.
