```
fire(service, me::Actor, event::Event)
```

Fire an event on the actor to be delivered by the actor's eventdispatcher.

To fire an event, the actor must have a field `eventdispatcher::Addr`, which will be filled automatically.
