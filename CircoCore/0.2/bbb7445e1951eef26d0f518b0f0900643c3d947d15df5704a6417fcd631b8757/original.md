```
OnDeath
```

Actor lifecycle message to release resources when the actor dies (meaning unscheduled "permanently").

The actor is still scheduled when this message is delivered, but no more messages will be delivered after this.
