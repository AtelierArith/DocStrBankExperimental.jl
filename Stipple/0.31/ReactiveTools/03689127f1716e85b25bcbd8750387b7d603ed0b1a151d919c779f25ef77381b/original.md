```
    @init(kwargs...)
```

Create a new app with the following kwargs supported:

  * `debounce::Int = JS_DEBOUNCE_TIME`
  * `throttle::Int = JS_THROTTLE_TIME`
  * `transport::Module = Genie.WebChannels`
  * `core_theme::Bool = true`

### Example

```
@app begin
  @in n = 10
  @out s = "Hello"
end

model = @init(debounce = 50)
```

---

```
    @init(App, kwargs...)
```

Create a new app of type `App` with the same kwargs as above

### Example

```
@app MyApp begin
  @in n = 10
  @out s = "Hello"
end

model = @init(MyApp, debounce = 50)
```
