```
smuggle([name]; basepath=basepath(), serializer=MsgPack)
```

Start a server using a UNIX sockets with a random name and `MsgPack.jl` as a serializer. The socket will be stored in `joinpath(basepath, name)`. If `name` is not provided, REPLSmuggler will try randomly generated names until a  non-already-existing socket name is found.

For example, on linux, you could find the socket in `/run/user/1000/julia/replsmuggler/clandestine_underworld` if the name was chosen to be `clandestine_underworld`.

The socket name is displayed in the REPL, and the server is accessible through [`CURRENT_SMUGGLER`](@ref).

See also [basepath](@ref).
