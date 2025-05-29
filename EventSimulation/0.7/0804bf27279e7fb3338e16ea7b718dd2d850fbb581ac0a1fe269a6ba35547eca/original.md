Resource type for holding numeric values (like amount of liquid). It stores current `quantity` of matter and its allowed `lo` and `hi` amounts. Servers can get matter from the resource with optional maximum number of requests pending for fulfillment.

Fields:

  * `quantity`       current quantity in resource
  * `lo`            minimum quantity of resource
  * `hi`            maximum quantity of resource
  * `fifo_requests` if `true` `requests` is FIFO, otherwise LIFO
  * `max_requests`  maximum `requests` size
  * `requests`      vector of request and requested quantity

Functions in `requests` must accept one argument `Scheduler`, so they should know the amount they requested. When resource arrives to a queue there is a try to immediately dispatch it to pending requests. When new request arrives there is a try to immediately fulfill it.

Initially an empty `SimResource` with no requests is constructed. Initial `quantity`, `lo` and `hi` may be provided. By default `SimResource` is empty, and has minimum quantity of zero and unbounded maximum.
