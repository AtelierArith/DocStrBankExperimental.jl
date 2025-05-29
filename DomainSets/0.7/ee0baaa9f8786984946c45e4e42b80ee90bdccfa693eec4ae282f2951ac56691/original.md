```
isequaldomain(d1, d2)
```

Are the two given domains equal?

Domains are considered equal if their membership functions return the same output for the same input.

It is not always possible to verify this automatically. If the result is `true`, then the domains are guaranteed to be equal. If the result is `false`, then either the domains are not equal or they are equal but the implementation fails to recognize this.
