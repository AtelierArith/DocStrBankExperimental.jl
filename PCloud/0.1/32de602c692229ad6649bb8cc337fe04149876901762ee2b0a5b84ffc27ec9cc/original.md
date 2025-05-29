```
oauth2_token(client::PCloudClient; kwargs...)
```

This method is used when an app is using the code flow. The app calls this method to obtain a bearer token, after the user had authorized the app.

This method expects the app's `key` and `secret`.

Also the `code` received from the redirect from oauth2_token is required.

Source: https://docs.pcloud.com/methods/oauth*2.0/oauth2*token.html

# Arguments

  * `client_id::String`: - id of the application
  * `client_secret::String`: - secret code for the application
  * `code::code`: - code returned to the redirect from authorize page

# Output

After the `code` is validted, the method returns the object with fields:

  * `access_token::String`: A token that could be used to call pCloud API methods.
  * `token_type::String`: The type of the token (always bearer).
  * `uid::Int`: The ID of the user, who gave access to the app.

# Output Example

```
{
    result: 0,
    access_token: "dghdghdj",
    token_type: "bearer",
    uid: 34535
}
```
