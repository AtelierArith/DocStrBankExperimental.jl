```
Web3Connection
```

EthereumノードへのJSON-RPC接続

```
    web3 = Web3Connection("http://localhost:8545")
    clientversion(web3) # -- クライアントバージョンを返す
    jsonget("http://localhost:8545", :web3_clientVersion, []) # -- clientversion(web3)と同等
    rawjsonget("http://localhost:8545", :web3_clientVersion, []) # -- 完全なJSONオブジェクトを返す
```
