```
Web3Connection
```

A JSON-RPC connection to an Ethereum node

```
    web3 = Web3Connection("http://localhost:8545")
    clientversion(web3) # -- return the client version
    jsonget("http://localhost:8545", :web3_clientVersion, []) # -- equivalent to clientversion(web3)
    rawjsonget("http://localhost:8545", :web3_clientVersion, []) # -- return full JSON object
```
