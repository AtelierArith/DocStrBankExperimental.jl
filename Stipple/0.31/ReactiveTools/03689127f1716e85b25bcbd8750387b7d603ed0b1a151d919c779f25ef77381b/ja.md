```
    @init(kwargs...)
```

次のkwargsをサポートする新しいアプリを作成します：

  * `debounce::Int = JS_DEBOUNCE_TIME`
  * `throttle::Int = JS_THROTTLE_TIME`
  * `transport::Module = Genie.WebChannels`
  * `core_theme::Bool = true`

### 例

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

上記と同じkwargsを持つ`App`タイプの新しいアプリを作成します

### 例

```
@app MyApp begin
  @in n = 10
  @out s = "Hello"
end

model = @init(MyApp, debounce = 50)
```
