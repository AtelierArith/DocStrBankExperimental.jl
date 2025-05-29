```
listtokens(client::PCloudClient; kwargs...)
```

Get a list with the currently active tokens associated with the current user.

Source: https://docs.pcloud.com/methods/auth/listtokens.html

# Output

Returns a list `tokens` of objectes full with token information. Every object has the fields:

  * `tokenid::Int`: identification number of the token.
  * `device::String`: information about the device to which the token was given.
  * `created::datetime`: when the token was created.
  * `expires_inactive::datetime`: when the token expires, if the owner does not use it.
  * `expires::datetime`: when the token expires. This is the latest moment, when the token will be active.

# Output Example

```
{
    "result": 0,
    "tokens": [
        {
            "tokenid": 163409641,
            "device": "User agent info",
            "created": "Mon, 09 Jun 2014 10:24:51 +0000"
            "expires_inactive": "Thu, 10 Jul 2014 10:24:51 +0000",
            "expires": "Tue, 09 Jun 2015 10:24:51 +0000",
        },

        ...

    ]    
}
```
