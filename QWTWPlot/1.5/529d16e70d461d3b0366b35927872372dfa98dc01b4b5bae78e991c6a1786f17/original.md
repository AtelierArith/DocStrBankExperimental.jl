```
qEnableCoordBroadcast(x::Vector{Float64}, y::Vector{Float64}, z::Vector{Float64}, time::Vector{Float64})
```

Enable UDP client.
 In case you'd like to connect to some external software from this library, it has UDP client and server inside. If/when you will move a marker, it will  broadcast 'marker information' via UDP. 
Other way should also work: if some other application will broadcast UDP with marker info, all the markers in this library supposed to be updated.

parameters: x, y,  and z are the vectors describing the line in 3D space; and 'time' is an additional time information, for every point of the line.

It will send out marker info to UDP port 49561.
Incoming (to this library) UDP  port number is 49562, and IP address is "127.0.0.1".

Incoming message format:  'CRDS"<x><y><z>"FFFF', where <x>, <y>, and <z> are  Float64 point coordinates, 8 bytes each, so this message contains 4 + 3*8 + 4 bytes
outgoing message format is approximately the same: "EEEE"<x><y><z>"FFFF"

If UDP client is enabled, server will also start. For all this to work, some firewall rules have to be added probably,  line 'allow 49561 and 49562 ports for the local host'.
