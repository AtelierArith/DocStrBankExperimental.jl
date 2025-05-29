```
@debounce fieldname ms

@debounce App fieldname ms
```

Set field-specific debounce time in ms.

### Parameters

  * `APP`: a subtype of ReactiveModel, e.g. `MyApp`
  * `fieldname`: fieldname òr fieldnames as written in the declaration, e.g. `x`, `(x, y, z)`
  * `ms`: debounce time in ms

### Example

#### Implicit apps

```
@app begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# no debouncing for fast messaging
@debounce quick 0

# long debouncing for long-running tasks
@debounce (slow1, slow2) 1000
```

#### Explicit apps

```
@app MyApp begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# no debouncing for fast messaging
@debounce MyApp quick 0

# long debouncing for long-running tasks
@debounce MyApp slow 1000
```
