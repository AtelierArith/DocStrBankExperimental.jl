```
create_client_with_mtls(cert_data, pk_data; kwargs...)
```

Create options configured for use with mutual TLS in client mode. Both buffers are treated as PKCS #7 PEM armored.

Arguments:

  * `cert_data (String)`: Certificate contents
  * `pk_data (String)`: Private key contents.
  * `ca_dirpath (Union{String,Nothing}) (default=nothing)`: Path to directory containing trusted certificates, which will overrides the default trust store. Only supported on Unix.
  * `ca_filepath (Union{String,Nothing}) (default=nothing)`: Path to file containing PEM armored chain of trusted CA certificates.
  * `ca_data (Union{String,Nothing}) (default=nothing)`: PEM armored chain of trusted CA certificates.
  * `alpn_list (Union{Vector{String},Nothing}) (default=nothing)`: If set, names to use in Application Layer Protocol Negotiation (ALPN). ALPN is not supported on all systems, see [`aws_tls_is_alpn_available`](https://octogonapus.github.io/LibAWSCRT.jl/dev/#LibAWSCRT.aws_tls_is_alpn_available-Tuple{}). This can be customized per connection; see [`TLSConnectionOptions`](@ref).
