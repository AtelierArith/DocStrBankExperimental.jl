```julia
connect(; ...)
connect(url; options...)

```

Connect to NATS server. The function is blocking until connection is initialized. In case of error during initialization process `connect` will throw exception if `retry_on_init_fail` is set to `false` (what is default). Otherwise handle will be returned and reconnect will continue in background.

Options are:

  * `verbose`: turns on protocol acknowledgements
  * `pedantic`: turns on additional strict format checking, e.g. for properly formed subjects
  * `tls_required`: indicates whether the client requires SSL connection
  * `tls_ca_path`: CA certuficate file path
  * `tls_cert_path`: client public certificate file
  * `tls_key_path`: client private certificate file
  * `auth_token`: client authorization token
  * `user`: connection username
  * `pass`: connection password
  * `name`: client name
  * `echo`: if set to `false`, the server will not send originating messages from this connection to its own subscriptions
  * `jwt`: the JWT that identifies a user permissions and account.
  * `no_responders`: enable quick replies for cases where a request is sent to a topic with no responders.
  * `nkey`: the public NKey to authenticate the client
  * `nkey_seed`: the private NKey to authenticate the client
  * `ping_interval`: interval in seconds how often server should be pinged to check connection health. Default is 120.0 seconds
  * `max_pings_out`: how many pings in a row might fail before connection will be restarted. Default is `2`
  * `retry_on_init_fail`: if set connection handle will be returned even if initial connect fails. Otherwise error causing failure will be trown. Default is `false`
  * `ignore_advertised_servers`: ignores other cluster servers returned by server. Default is `false`
  * `retain_servers_order`: try to connect server in order specified in `url` or list returned by the server. Defaylt is `false`
  * `send_enqueue_when_disconnected`: allows buffering outgoing messages during disconnection. Default is `true`
  * `reconnect_delays`: vector of delays that reconnect is performed until connected again, by default it will try to reconnect every second without time limit.
  * `send_buffer_limit`: soft limit for buffer of messages pending. Default is `2097152` bytes, if too small operations that send messages to server (e.g. `publish`) may throw an exception
  * `drain_timeout`: Timeout for drain process. After timeout in case of not everyting is processed drain will stop and error will be reported.
  * `drain_poll`: Interval for `drain` to check if all messages in buffers are processed.
