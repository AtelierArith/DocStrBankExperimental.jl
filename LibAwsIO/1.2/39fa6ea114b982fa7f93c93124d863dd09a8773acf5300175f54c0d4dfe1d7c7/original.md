```
aws_channel_trigger_read(channel)
```

A way for external processes to force a read by the data-source channel handler. Necessary in certain cases, like when a server channel finishes setting up its initial handlers, a read may have already been triggered on the socket (the client's CLIENT_HELLO tls payload, for example) and absent further data/notifications, this data would never get processed.

### Prototype

```c
int aws_channel_trigger_read(struct aws_channel *channel);
```
