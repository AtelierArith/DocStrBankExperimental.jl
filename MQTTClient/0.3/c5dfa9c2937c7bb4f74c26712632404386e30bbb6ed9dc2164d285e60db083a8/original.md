```
Configuration
```

Container for the mqtt client and mqtt connection data. This is partially iterable, and can be spread to 2 variables with the `...` splat operator or `client, conn = conf` variable assignment.

## Example

```julia
# using the MakeConnection interface function
config = MakeConnection("/temp/mqtt.sock")

# using a defined IO
io = IOConnection("localhost", 1883)
config = Configuration(io)

# spreading the variables
client, connection = Configuration(...)
```
