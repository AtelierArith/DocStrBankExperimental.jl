```julia
publish(connection, subject; ...)
publish(connection, subject, data; reply_to)

```

Publish `data` to a `subject`, payload is obtained with `show` method taking `mime` `application/nats-payload`, headers are obtained with `show` method taking `mime` `application/nats-headers`.

There are predefined convertion defined for `String` type. To publish headers there is defined conversion from tuple taking vector of pairs of strings.

Optional parameters:

  * `reply_to`: subject to which a result should be published

Examples:

```
    publish(nc, "some_subject", "Some payload")
    publish("some_subject", ("Some payload", ["some_header" => "Example header value"]))
```
