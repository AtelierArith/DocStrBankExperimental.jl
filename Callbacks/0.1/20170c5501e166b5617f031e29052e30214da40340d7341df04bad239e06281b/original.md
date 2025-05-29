Capture a vector of value of type `T`

```julia
function f(x; cb)
  for i = 1:10
    x += 0.0
    cb(x)
  end
end

cb, xs = capturevals(:x)
f(0.5; cb = cb)
```
