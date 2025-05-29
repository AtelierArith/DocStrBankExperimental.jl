```
get_authorization()::Authorization
```

Get an authorization token. This function first looks for an environment values `DROPBOXSDK_ACCESS_TOKEN`, and then for a file `secrets.http` in the current directory. If neither exists, this is an error.
