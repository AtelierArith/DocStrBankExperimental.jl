```
wait_until_done(ctx::Context, rsp::TransactionResponse) -> TransactionResponse
wait_until_done(ctx::Context, transaction) -> TransactionResponse
wait_until_done(ctx::Context, txn_id::String) -> TransactionResponse
```

Block until the `transaction` has reached a terminal state, and return the response.

Continuously polls get_transaction() for the transaction's state, until the transaction has finished. A transaction has finished once it has reached one of the terminal states: `COMPLETED` or `ABORTED`. The polling uses a low-overhead exponential backoff in order to ensure low-latency results without overloading network traffic.
