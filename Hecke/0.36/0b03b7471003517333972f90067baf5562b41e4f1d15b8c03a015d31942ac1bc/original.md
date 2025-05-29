```
annihilator(a::ResElem{ZZRingElem}) -> r
annihilator(a::ResElem{Integer}) -> r
```

The annihilator of $a$, i.e. a generator for the annihilator ideal $\{x | xa = 0\} = \langle r\rangle$.
