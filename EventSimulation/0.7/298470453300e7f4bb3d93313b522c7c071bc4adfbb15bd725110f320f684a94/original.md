SimQueue type for holding arbitrary objects `O`. It allows objects to be waiting in a queue with optional maximum queue size. Servers can get objects from the queue with optional maximum number of requests pending for fulfillment.

Fields:

  * `fifo_queue`    if `true` `queue` is FIFO, otherwise LIFO
  * `max_queue`     maximum `queue` size
  * `queue`         vector of objects in a queue
  * `fifo_requests` if `true` `requests` is FIFO, otherwise LIFO
  * `max_requests`  maximum `requests` size
  * `requests`      vector of request functions

Functions in `requests` must accept two arguments `Scheduler` and `O`. When `O` arrives to a queue there is a try to immediately feed it to pending requests. When new request arrives there is a try to immediately provide it with `O`.

Initially an empty `SimQueue` with no requests is constructed. By default `queue` and `requests` have FIFO policy and are unbounded.
