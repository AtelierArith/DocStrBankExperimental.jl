```
connect_gsheet(client_id::String, client_secret::String; redirect_uri::String = "http://localhost:8081")
```

Connects to Google Sheets API by obtaining an access token using OAuth 2.0 authorization flow. To obtain the credentials, go to the Google Cloud Console -> APIs and Services -> Credentials -> Create Credentials -> Create OAuth Client ID -> Desktop App.  This will contain the `client_id` and `client_secret`

# Arguments

  * `client_id::String`: The client ID obtained from the Google Cloud Console.
  * `client_secret::String`: The client secret obtained from the Google Cloud Console.
  * `redirect_uri::String`: The URI to which the authorization server will redirect the user after granting access. Defaults to "http://localhost:8081".

# Returns

  * An instance of `GSheetAuth` containing the client ID, client secret, redirect URI, and access token.

# Example

```julia
julia> connect_gsheet("your_client_id", "your_client_secret")
```
