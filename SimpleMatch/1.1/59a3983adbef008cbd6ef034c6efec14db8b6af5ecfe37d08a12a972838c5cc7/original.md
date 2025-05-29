matches arguments against locally created function and returns match

Simple match implementation which uses a locally created function.   This gives a very familiar syntax and is natural to use.

Example

```
a = 1
b = 2.0
matched = @match(a, b) do f
  f(::Int, ::AbstractFloat) = b + 3
  f(_...) = a + 9
end
# 5.0
```

We need to define this as macro, as it turns out to be relatively difficult   to define a function within an anonymous do notation
