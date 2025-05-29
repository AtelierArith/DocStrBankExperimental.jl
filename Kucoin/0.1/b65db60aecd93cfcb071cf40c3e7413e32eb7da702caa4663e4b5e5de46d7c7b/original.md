Kucoin.get*ws*token([api_data]) -> JSON3.Object

Apply for a websocket connection token. See Kucoin official  [docs](https://docs.kucoin.com/#apply-connect-token) for more details.

# Arguments

  * `api_data::UserApiData`: [Optional] holds API data susch as api key, secret, passphrase,

etc. If absent returns a token that can be used only with public channels.

# Returns

  * `JSON3.Object`

```json
{
  "instanceServers": [
    {
      "endpoint": "wss://push1-v2.kucoin.com/endpoint",
      "protocol": "websocket",
      "encrypt": true,
      "pingInterval": 50000,
      "pingTimeout": 10000
    }
  ],
  "token": "vYNlCtbz4XNJ1QncwWilJnBtmmfe4geLQDUA62kK=="
}
```
