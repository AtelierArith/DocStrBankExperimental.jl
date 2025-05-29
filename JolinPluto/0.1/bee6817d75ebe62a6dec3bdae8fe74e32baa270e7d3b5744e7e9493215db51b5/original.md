```
authenticate_token()
authenticate_token("exampleaudience")
```

Creates a JSON Web Token which can be used for authentication at common cloud providers.

On cloud.jolin.io the token will be issued and signed by cloud.jolin.io, on Github Actions (used for automated tests), a respective github token is returned.
