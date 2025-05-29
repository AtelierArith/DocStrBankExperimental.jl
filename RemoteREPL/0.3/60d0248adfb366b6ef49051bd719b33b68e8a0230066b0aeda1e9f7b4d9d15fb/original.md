```
@remote ex
```

Execute expression `ex` on the other side of the current RemoteREPL connection and return the value.

This can be used in both directions:

1. From the normal `julia>` prompt, execute `ex` on the remote server and return the value to the client.
2. From a remote prompt, execute `ex` on the *client* and push the resulting value to the remote server.

# Examples

Push a value from the client to the server:

```
julia> client_val = 1:100;

julia@localhost> server_val = @remote client_val
1:100
```

Fetch a pair of variables `(x,y)` from the server, and plot them on the client with a single line:

```
# In two lines
julia> x,y = @remote (x, y)
       plot(x, y)

# Or as a single expression
julia> plot(@remote((x, y))...)
```
