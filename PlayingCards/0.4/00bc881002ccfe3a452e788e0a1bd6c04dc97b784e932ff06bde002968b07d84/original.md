```
Card
```

Encode a playing card as a 6-bit integer (low bits of a `UInt8`):

  * low bits represent rank from 0 to 15
  * high bits represent suit (♣, ♢, ♡ or ♠)

Ranks are assigned as follows:

  * numbered cards (2 to 10) have rank equal to their number
  * jacks, queens and kings have ranks 11, 12 and 13
  * there are low and high aces with ranks 1 and 14, 0 is for Joker
  * there are low and high jokers with ranks 0 and 15

This allows any of the standard orderings of cards ranks to be achieved simply by choosing which aces to use.

There are a total of 64 possible card values with this scheme, represented by `UInt8` values `0x00` through `0x3f`.
