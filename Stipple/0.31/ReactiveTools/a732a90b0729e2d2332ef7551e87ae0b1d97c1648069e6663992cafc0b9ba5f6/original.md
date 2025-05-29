```
@clear_debounce

@clear_debounce fieldname

@clear_debounce App

@clear_debounce App fieldname
```

Clear field-specific debounce time, for setting see `@debounce`. After calling `@clear debounce` the field will be debounced by the value given in the `@init` macro.

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
@debounce slow 1000

# reset to standard value of the app
@clear_debounce quick

# clear all field-specific debounce times
@clear_debounce
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

@clear_debounce MyApp quick

# clear all field-specific debounce times
@clear_debounce MyApp
```
