```
eachpoint(message::Message)
```

Iterate through each point in the message, returning the lon, lat, and value.

# Example

```Julia
for (lon, lat, val) in eachpoint(message)
    println("Value at ($lat, $lon) is $val")
end
```
