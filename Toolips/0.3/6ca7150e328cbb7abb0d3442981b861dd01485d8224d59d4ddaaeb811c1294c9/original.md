```julia
struct IP4 <: Identifier
```

  * `ip`**::String**
  * `port`**::UInt16**

An `IPv4` is the " fourth" iteration of the internet protocol, which assigns  IP addresses to computers via an Internet Service Provider (ISP) and DHCP (a router server.)  `Toolips` IPs are written just how they are seen other than the address being a `String`.

```example
host = "127.0.0.1":8000
```

```julia
IP4(ip::Abstractstring, port::Integer)
```

  * See also: `start!`, `Toolips`, `route`, `route!`
