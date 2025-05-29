```
aws_retry_strategy_new_standard(allocator, config)
```

This is a retry implementation that cuts off traffic if it's detected that an endpoint partition is having availability problems. This is necessary to keep from making outages worse by scheduling work that's unlikely to succeed yet increases load on an already ailing system.

We do this by creating a bucket for each partition. A partition is an arbitrary specifier. It can be anything: a region, a service, a combination of region and service, a literal dns name.... doesn't matter.

Each bucket has a budget for maximum allowed retries. Different types of events carry different weights. Things that indicate an unhealthy partition such as transient errors (timeouts, unhealthy connection etc...) cost more. A retry for any other reason (service sending a 5xx response code) cost a bit less. When a retry is attempted this capacity is leased out to the retry. On success it is released back to the capacity pool. On failure, it remains leased. Operations that succeed without a retry slowly restore the capacity pool.

If a partition runs out of capacity it is assumed unhealthy and retries will be blocked until capacity returns to the pool. To prevent a partition from staying unhealthy after an outage has recovered, new requests that succeed without a retry will increase the capacity slowly ( a new request gets a payback lease of 1, but the lease is never actually deducted from the capacity pool).

### Prototype

```c
struct aws_retry_strategy *aws_retry_strategy_new_standard( struct aws_allocator *allocator, const struct aws_standard_retry_options *config);
```
