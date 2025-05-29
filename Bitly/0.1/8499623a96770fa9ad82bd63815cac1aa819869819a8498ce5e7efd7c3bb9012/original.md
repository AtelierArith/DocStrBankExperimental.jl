A connection to the Bitly API.

## Constructors

  * `BitlyToken()`: Token detected automatically. First, looks for the environment variable

`BITLY_ACCESS_TOKEN`, then looks for the file `~/.bitlyrc`.

  * `BitlyToken(token::AbstractString)`: User specifies token directly

See [`requestBitlyToken`](@ref).
