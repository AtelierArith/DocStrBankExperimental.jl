```
poll_for_event(conn:: XCBConnection) -> Union{(XCBEvent, Bool), Nothing}
```

Pop an event from the queue of received events. Returns the event and whether it was sent using the SendEvent request, or `nothing` if no events are queued.
