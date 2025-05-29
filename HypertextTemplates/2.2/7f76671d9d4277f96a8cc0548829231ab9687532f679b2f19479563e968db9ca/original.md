```
SafeString(str)
```

A string type that bypasses the default HTML escaping that is applied to all strings rendered with `@render` and DOM element properties. Only apply this type to string values that are not user-defined. If applying this to user-defined values ensure that proper sanitization has been carried out.
