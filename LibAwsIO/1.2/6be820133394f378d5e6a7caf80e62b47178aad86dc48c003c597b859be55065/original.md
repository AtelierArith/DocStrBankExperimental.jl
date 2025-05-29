```
aws_host_resolver_new_default(allocator, options)
```

Creates a host resolver with the default behavior. Here's the behavior:

Since there's not a reliable way to do non-blocking DNS without a ton of risky work that would need years of testing on every Unix system in existence, we work around it by doing a threaded implementation.

When you request an address, it checks the cache. If the entry isn't in the cache it creates a new one. Each entry has a potentially short lived back-ground thread based on ttl for the records. Once we've populated the cache and you keep the resolver active, the resolution callback will be invoked immediately. When it's idle, it will take a little while in the background thread to fetch more, evaluate TTLs etc... In that case your callback will be invoked from the background thread.

---

A few things to note about TTLs and connection failures.

We attempt to honor your max ttl but will not honor it if dns queries are failing or all of your connections are marked as failed. Once we are able to query dns again, we will re-evaluate the TTLs.

Upon notification connection failures, we move them to a separate list. Eventually we retry them when it's likely that the endpoint is healthy again or we don't really have another choice, but we try to keep them out of your hot path.

---

Finally, this entire design attempts to prevent problems where developers have to choose between large TTLs and thus sticky hosts or short TTLs and good fleet utilization but now higher latencies. In this design, we resolve every second in the background (only while you're actually using the record), but we do not expire the earlier resolved addresses until max ttl has passed.

This for example, should enable you to hit thousands of hosts in the Amazon S3 fleet instead of just one or two.

### Prototype

```c
struct aws_host_resolver *aws_host_resolver_new_default( struct aws_allocator *allocator, const struct aws_host_resolver_default_options *options);
```
