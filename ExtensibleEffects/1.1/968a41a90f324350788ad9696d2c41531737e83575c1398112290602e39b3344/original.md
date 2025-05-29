```
ContextManagerHandler(continuation)
```

Handler for `DataTypesBasic.ContextManager`.

The naive handler implementation for contextmanager would immediately run the continuation within the contextmanager. However this does not work, as handling one effect does not mean that all "inner" effects are already handled. Hence, such a handler would actually initialize and finalize the contextmanager, without its value being processed already. When the other "inner" effects are run later on, they would find an already destroyed contextmanager session. We need to make sure, that the contextmanager is really the last Effect run. Therefore we create a custom handler.
