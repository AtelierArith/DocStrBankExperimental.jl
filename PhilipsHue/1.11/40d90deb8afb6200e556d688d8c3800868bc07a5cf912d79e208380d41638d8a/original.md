```
register(bridge_ip; devicetype="juliascript", blankusername="")
```

Register the devicetype and username with the bridge.

Quoth Philips: If the username is not provided, a random key will be generated and returned in the response. Important! The username will soon be deprecated in the bridge. It is strongly recommended not to use this and use the randomly generated bridge username.

So we'll return the randomly generated key, or "" on failure.
