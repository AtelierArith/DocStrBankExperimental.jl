```
Client(
    token::String
    application_id::Snowflake
    intents::Int;
    presence::Union{Dict, NamedTuple}=Dict(),
    strategies::Dict{DataType, <:CacheStrategy}=Dict(),
    version::Int=9,
) -> Client
```

A Discord bot. `Client`s can connect to the gateway, respond to events, and make REST API calls to perform actions such as sending/deleting messages, kicking/banning users, etc.

### Bot Token

A bot token can be acquired by creating a new application [here](https://discordapp.com/developers/applications). Make sure not to hardcode the token into your Julia code! Use an environment variable or configuration file instead.

### Application ID

The application id for your bot can be found [here](https://discordapp.com/developers/applications).  Make sure not to hardcode the application id into your Julia code!  Use an environment variable or configuration file instead.

### Intents

Integer representing intents. More information [here](https://discord.com/developers/docs/topics/gateway#gateway-intents).

### Presence

The `presence` keyword sets the bot's presence upon connection. It also sets defaults for future calls to [`set_game`](@ref). The schema [here](https://discordapp.com/developers/docs/topics/gateway#update-status-gateway-status-update-structure) must be followed.

### Cache Control

By default, most data that comes from Discord is cached for later use. However, to avoid memory leakage, not all of it is kept forever. The default setings are to keep everything but [`Message`](@ref)s, which are deleted after 6 hours, forever. Although the default settings are sufficient for most workloads, you can specify your own strategies per type with the `strategies` keyword. Keys can be any of the following:

  * [`Guild`](@ref)
  * [`DiscordChannel`](@ref)
  * [`Message`](@ref)
  * [`User`](@ref)
  * [`Member`](@ref)
  * [`Presence`](@ref)

For potential values, see [`CacheStrategy`](@ref).

The cache can also be disabled/enabled permanently and temporarily as a whole with [`enable_cache!`](@ref) and [`disable_cache!`](@ref).

### API Version

The `version` keyword chooses the Version of the Discord API to use. Using anything but `9` is not officially supported by the Ekztazy.jl developers.

### Sharding

Sharding is handled automatically. The number of available processes is the number of shards that are created. See the [sharding example](https://github.com/Xh4H/Discord.jl/blob/master/examples/sharding.jl) for more details.
