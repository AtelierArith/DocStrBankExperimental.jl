```
@v blob.x[2].y
```

Get the *value* at `blob.x[2].y`.

```
@v blob.x[2].y = 42
```

Set the *value* at `blob.x[2].y`.

NOTE macros bind tightly, so:

```
# invalid syntax
@v blob.x[2].y < 42

# valid syntax
(@v blob.x[2].y) < 42
```
