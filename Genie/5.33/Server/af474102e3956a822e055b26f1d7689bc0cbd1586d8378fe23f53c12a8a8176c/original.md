```
down(; webserver::Bool = true, websockets::Bool = true) :: ServersCollection
```

Shuts down the servers optionally indicating which of the `webserver` and `websockets` servers to be stopped. It does not remove the servers from the `SERVERS` collection. Returns the collection.
