```
session = AzSession([; kwargs...])
```

Create an Azure session for authentication using a specific authentication protocol.  The available protocols and their `kwargs` are as follows.

## Authorization code flow

```julia
session = AzSession(;
    protocol = _manifest["protocol"] | AzDeviceCodeFlowCredentials,
    client_id = AzSessions._manifest["client_id"],
    redirect_uri = "http://localhost:44300/reply",
    scope = "openid+offline_access+https://storage.azure.com/user_impersonation",
    scope_auth = "openid+offline_access+https://management.azure.com/user_impersonation+https://storage.azure.com/user_impersonation",
    tenant = AzSessions._manifest["tenant"],
    lazy = false,
    clearcache = false)
```

## Device code flow

```julia
session = AzSession(;
    protocol = AzDeviceCodeCredentials
    client_id = AzSessions._manifest["client_id"],
    scope = "openid+offline_access+https://management.azure.com/user_impersonation",
    scope_auth = "openid+offline_access+https://management.azure.com/user_impersonation+https://storage.azure.com/user_impersonation",
    tenant = AzSessions._manifest["tenant"],
    clearcache = false)
```

## Client Credentials

```julia
session = AzSession(;
    protocol = AzClientCredentials,
    tenant=AzSessions._manifest["tenant"],
    client_id=AzSessions._manifest["client_id"],
    client_secret=AzSessions._manifest["client_secret"],
    resource="https://management.azure.com/",
    clearcache = false)
```

## VM Credentials

```julia
session = AzSession(;
    protocol = AzVMCredentials,
    resource = "https://management.azure.com/",
    clearcache = false)
```

## New audience

Create a session from an existing auth code flow session or device code flow session, but with a new scope.  This means that we can get a session with a new audience without requiring re-authentication.  Note that the new scope must be in `session.scope_auth`.

```julia
session = AzSession(;
    protocol=AzAuthCodeFlowCredentials,
    scope_auth="openid+offline_access+https://management.azure.com/user_impersonation+https://storage.azure.com/user_impersonation",
    scope="openid+offline_access+https://management.azure.com/user_impersonation")

t = token(session) # token for `https://management.azure.com` audience
session = AzSession(session; scope="openid+offline_access+https://storage.azure.com/user_impersonation")
t = token(session) # token for `https://storage.azure.com` audience without needing to re-authenticate
```

# Notes

  * If `lazy=false`, then authenticate at the time of construction.  Otherwise, wait until the first use of the session before authenticating.
  * If `clearcache=false`, then check the session-cache for an existing token rather than re-authenticating.  The cache is stored in a JSON file (`~/.azsessions/sessions.json`).
  * The default protocol can be set in the manifest (see the `AzSessions.write_manifest` method for more information).
