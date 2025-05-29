```
getfreeinfo( msg::AbstractString
           , mode::Mode
           , eclevel::ErrCorrLevel
           , version::Int)
```

空きブロックの数と部分空きブロックのバイト数を返します。

## 背景

1. 必要なビット  requiredbits = mode indicator # 4 ビット               + ccindicator(mode, version)              + databits(msg, mode)              + padbits # 空きビット(* 重要)              = 8 * (nb1 * nc1 + nb2 * nc2)
2. メッセージブロックと誤り訂正ブロック

      * メッセージブロックは必要なビットから分割されます
      * 各msgblockはecblockに関連付けられています
3. メッセージビット  messagebits = msgblocks + ecblocks + 残りのビット
