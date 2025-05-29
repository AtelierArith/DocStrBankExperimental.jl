```
TLSConnectionOptions(
    client_tls_context::ClientTLSContext,
    alpn_list::Union{Vector{String},Nothing} = nothing,
    server_name::Union{String,Nothing} = nothing,
)
```

Connection-specific TLS options. Note that while a TLS context is an expensive object, this object is cheap.

Arguments:

  * `client_tls_context (ClientTLSContext)`: TLS context. A context can be shared by many connections.
  * `alpn_list (Union{Vector{String},Nothing}) (default=nothing)`: Connection-specific Application Layer Protocol Negotiation (ALPN) list. This overrides any ALPN list on the TLS context in the client this connection was made with. ALPN is not supported on all systems, see [`aws_tls_is_alpn_available`](https://octogonapus.github.io/LibAWSCRT.jl/dev/#LibAWSCRT.aws_tls_is_alpn_available-Tuple%7B%7D).
  * `server_name (Union{String,Nothing}) (default=nothing)`: Name for TLS Server Name Indication (SNI). Also used for x.509 validation.
