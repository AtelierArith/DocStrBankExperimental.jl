TD_auth()

run authentication procedure

1. already authenticated -> do nothing
2. access token expired && has refresh token -> refresh access token
3. refresh token expired -> get refresh token
4. no CONSUMER_KEY -> error
