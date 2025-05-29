`@vars(expr)`

```
@vars MyDashboard begin
  a::Int = 1
  b::Float64 = 2
  c::String = "Hello"
  d::String = "readonly", NON_REACTIVE, READONLY
  e::String = "private",  NON_REACTIVE, PRIVATE
end
```
