```
abmqueue(model::EventQueueABM)
```

Return the queue of scheduled events in the `model`. The queue maps two integers (agent id, event index) to the time the event will occur, in absolute time.
