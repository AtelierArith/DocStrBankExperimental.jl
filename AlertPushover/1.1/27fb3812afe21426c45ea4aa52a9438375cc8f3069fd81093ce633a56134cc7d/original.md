```
pushover_alert!(;token,user)
```

Use the [Pushover](https://pushover.net) notificaiton service to send notifications when calling `alert`. You must provide an API and user token, which are documented in the [description of pushover's api](https://pushover.net/api).

Call this funciton with no arguments to return to the default alert notification backend.
