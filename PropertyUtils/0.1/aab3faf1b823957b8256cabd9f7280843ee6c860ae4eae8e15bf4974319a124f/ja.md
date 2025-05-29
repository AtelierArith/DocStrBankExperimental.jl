```
fields(x)
```

`getproperty`を`getfield`にマップします。

# 例

```
struct A
    x::Int
end
Base.getproperty(a::A, x::Symbol) = "hello"

a = A(1)
a.x == "hello"

fields(a).x == 1
```
