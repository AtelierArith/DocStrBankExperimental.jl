```
userinfo(client::PCloudClient; kwargs...)
```

Returns information about the current user. As there is no specific `login` method as credentials can be passed to any method, this is an especially good place for logging in with no particular action in mind.

Source: https://docs.pcloud.com/methods/general/userinfo.html

# Output

  * `email::String`: email address of the user
  * `emailverified::Bool`: true if the user had verified it's email
  * `registered::datetime`: when the user was registerd
  * `premium::Bool`: true if the user is premium
  * `premiumexpires::datetime`: if premium is true: premiumexpires will be the date until the service is
  * `quota::Int`: in bytes
  * `usedquota::Int`: in bytes, so quite big numbers
  * `language::String`: 2-3 characters lowercase languageid

# Output Example

```
{
    result: 0, 
    userid: 1234,
  email: pcloud@pcloud.com,
  emailverified: true,
  registered: "Mon, 18 Nov 2013 15:32:05 +0000",
  language: "en",
    premium: false,
  usedquota: 500,
  quota: 1000    
}
```
