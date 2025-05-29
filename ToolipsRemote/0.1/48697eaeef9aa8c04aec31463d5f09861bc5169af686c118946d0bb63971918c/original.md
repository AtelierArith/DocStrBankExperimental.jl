### Remote <: Toolips.ServerExtension

  * type::Vector{Symbol}
  * remotefunction::Dict{Int64, Function}
  * f::Function
  * logins::Dict{String, Hash}
  * users::Dict{Vector{UInt8}, String}
  * access::Dict{String, Int64}
  * motd::String - A message to be shown at the login screen.

The remote extension makes it possible to connect to your server from another Julia REPL. Can be provided with an alternative remote function as the first positional argument, as well as a new serving function as the second positional argument. A remote function should take a Connection and a String. A serving function should take only a Connection. `remotefunction` is a `Dict`     which will take levels as keys and functions as values. We then set such keys     in the `usernames` Vector. This Vector is a Vector{Pair{String, Pair{String, Int64}}}.     See the constructors below for an example. The functions provided to `remotefunction`     should take a `RemoteConnection` or `Toolips.AbstractConnection`

##### example

```
r = Remote()
st = ServerTemplate(extensions = [Remote()])
```

---

##### constructors

Remote(remotefunction::Function = Dict{Int64, Function}(1 => controller()), usernames::Vector{Pair{String, Pair{String, Int64}}} = ["root" => "1234" => 1];         motd::String, serving_f::Function)
