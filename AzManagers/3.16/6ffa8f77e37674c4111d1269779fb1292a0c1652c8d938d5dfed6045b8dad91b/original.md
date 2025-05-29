```
nworkers_provisioned([service=false])
```

Count of the number of scale-set machines that are provisioned regardless of their status within the Julia cluster.  If `service=true`, then we use the Azure scale-set service to make the count, otherwise we use client side book-keeeping.  The later is useful to avoid making too many requests to the Azure scale-set service, causing it to throttle future responses.
