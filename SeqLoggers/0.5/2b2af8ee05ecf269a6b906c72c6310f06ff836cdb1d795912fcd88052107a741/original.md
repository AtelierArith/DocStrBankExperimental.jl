```
SeqLogger(
    server_url::AbstractString;
    min_level::Logging.LogLevel=Logging.Info,
    api_key::AbstractString="",
    batch_size::Int=10,
    event_properties...
)
```

Logger to post log events to a `Seq` log server.

### Inputs

  * `server_url` – `Seq` server url (e.g. `"http://localhost:5341"`)
  * `min_level` – (optional, `default=Logging.Info`) minimal log level to filter the log events
  * `api_key` –  (optional, `default=""`) API-key string for registered Applications
  * `batch_size` – (optional, `default=10`) number of log events sent to `Seq` server in single post
  * `event_properties` – (optional) global log event properties

#### Global Log Event Properties

The `SeqLogger` constructor allows to add global log event properties to the logger using   keyword-arguments.

```julia
SeqLogger("http://localhost:5341"; App="DJSON", Env="PROD", Id="24e0d145-d385-424b-b6ec-081aa17d504a")
```

#### Local Log Event Properties

For each individual log event, additional log event properties can be added which only apply to a single log event.

```julia
@info "Log additional user id {userId}" userId="1"
```

Note: This only works, if the [`Logging.current_logger`](@ref) is of type `SeqLogger` or "contains" a `SeqLogger`.
