User-supplied transform callback which implements the proxy request flow and ultimately, across all execution pathways, invokes either the terminate function or the forward function appropriately.

For tunneling proxy connections, this request flow transform only applies to the CONNECT stage of proxy connection establishment.

For forwarding proxy connections, this request flow transform applies to every single http request that goes out on the connection.

Forwarding proxy connections cannot yet support a truly async request transform without major surgery on http stream creation, so for now, we split into an async version (for tunneling proxies) and a separate synchronous version for forwarding proxies. Also forwarding proxies are a kind of legacy dead-end in some sense.
