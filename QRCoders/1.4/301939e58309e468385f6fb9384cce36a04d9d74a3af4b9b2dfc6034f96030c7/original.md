```
getfreeinfo( msg::AbstractString
           , mode::Mode
           , eclevel::ErrCorrLevel
           , version::Int)
```

Return the number of free blocks and the number of bytes of the partial-free block.

## Background

1. required bits  requiredbits = mode indicator # 4 bits               + ccindicator(mode, version)              + databits(msg, mode)              + padbits # free bits(* important)              = 8 * (nb1 * nc1 + nb2 * nc2)
2. messge block and error correction block

      * message blocks are splited from required bits
      * each msgblock is associated with an ecblock
3. message bits  messagebits = msgblocks + ecblocks + remainder bits
