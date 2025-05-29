```
Computes all batch element losses. Picks the batch element with the greatest accumulated loss as next training element. If picked, accumulated loss is resetted.
(Prevents starvation of batch elements with little loss)
```
