```
authorize(client::PCloudClient; kwargs...)
```

This is a web page which starts the OAuth 2.0 authorization flow. On this page he user logs in to pCloud and then desides if to grant the access to your app.

After the user takes the decision to give or not access from your application to his profile information and personal data, they will be redirected to the URI specified bv `redirect_uri`.

OAuth 2.0 has two different authorization flows:

*Code flow* - returns a `code` via the `redirect_uri` redirect. This code after that should be converted inot a `bearer token` using oauth2_token method.

*Token (implicit) flow* - returns the `bearer token` via the `redirect_uri` redirect. It does not rquires your app to initiate a second call to pCloud API.

*Code flow* is recommended if the app is using a server.

*Token flow* is appropriate for pure client-side apps - such for mobile devices or based only on JavaScript.

Source: https://docs.pcloud.com/methods/oauth_2.0/authorize.html

# Arguments

  * `client_id::String`: id of the app.
  * `response_type::String`: code or token.

# Optional Arguments

  * `redirect_uri::String`: where to redirect after approval, mandatory for token, optional for code (code will be displayed to the user in this case).
  * `state::String`: opaque data that will be passed back to redirect_uri.
  * `force_reapprove::Bool`: if set, will force re-approval even if the application is already approved by the user.
  * `permissions::manageshares`: a comma (,) separated list. If set additional permissions will appear in the approval form. Currently the only option is

# Output

On approval redirects to:

*Code flow*

These parameters are pased in the query string (after ?)

  * `code::String`: The authorization code that could be exchanged for a bearer token by calling oauth2_token
  * `state::String`: The contents of the state parameter, that was passed.

redirect_uri?code=XXXXX&state=YYYYY

*Token flow*

These parameters are pased in the URI fragment (after #)- `access_token::String`: A token that could be used to call pCloud API methods.

  * `token_type::String`: The type of the token (always bearer).
  * `uid::Int`: The ID of the user, who gave access to the app.
  * `state::String`: The contents of the state parameter, that was passed.

redirect*uri#access*token=XXXXX&token_type=bearer&

uid=11111&state=YYYYYY
