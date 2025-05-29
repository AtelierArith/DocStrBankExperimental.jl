```
@clear_throttle

@clear_throttle fieldname

@clear_throttle App

@clear_throttle App fieldname
```

Clear field-specific throttle time, for setting see `@throttle`. After calling `@clear throttle` the field will be throttled by the value given in the `@init` macro.

### Example

#### Implicit apps

```
@app begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end


# set standard throttle time for all fields
@page("/", ui, model = MyApp, throttle = 100)

# no throttling for fast messaging
@throttle quick 0
@throttle slow 1000

# reset to standard value of the app
@clear_throttle quick

# clear all field-specific throttle times
@clear_throttle
```

#### Explicit apps

```
@app MyApp begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# set standard throttle time for all fields
@page("/", ui, model = MyApp, throttle = 100)

# no throttling for fast messaging
@throttle MyApp quick 0

@clear_throttle MyApp quick

# clear all field-specific throttle times
@clear_throttle MyApp
```
