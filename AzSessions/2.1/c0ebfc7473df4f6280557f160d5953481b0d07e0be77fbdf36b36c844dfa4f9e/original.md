```
token(session[; offset=Second(rand(300:600))])
```

Return the OAuth2 token associate with `session`.  The `offset` ensures that the token is valid for at least `offset` time.  The default offset is randomized between 5 and 15 minutes.  We randomize the offset to avoid calling the Azure authentication end-point at the same time from many VMs operating in parallel.
