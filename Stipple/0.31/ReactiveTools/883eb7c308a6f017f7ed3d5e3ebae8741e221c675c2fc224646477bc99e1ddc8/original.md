```
@throttle fieldname ms

@throttle App fieldname ms
```

Set field-specific throttle time in ms.

### Parameters

  * `APP`: a subtype of ReactiveModel, e.g. `MyApp`
  * `fieldname`: fieldname òr fieldnames as written in the declaration, e.g. `x`, `(x, y, z)`
  * `ms`: throttle time in ms

### Example

#### Implicit apps

```
@app begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# no throttling for fast messaging
@throttle quick 0

# long throttling for long-running tasks
@throttle (slow1, slow2) 1000
```

#### Explicit apps

```
@app MyApp begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# no throttling for fast messaging
@throttle MyApp quick 0

# long throttling for long-running tasks
@throttle MyApp slow 1000
```
