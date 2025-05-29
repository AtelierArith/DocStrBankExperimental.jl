```
fields(x)
```

Map `getproperty` to `getfield`.

# Example

```
struct A
    x::Int
end
Base.getproperty(a::A, x::Symbol) = "hello"

a = A(1)
a.x == "hello"

fields(a).x == 1
```
