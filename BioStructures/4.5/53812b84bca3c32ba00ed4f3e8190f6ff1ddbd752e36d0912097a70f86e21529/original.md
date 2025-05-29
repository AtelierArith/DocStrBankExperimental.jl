```
resid(res; full=true)
```

Get a descriptive residue ID `String` for an `AbstractAtom` or `AbstractResidue`.

Format is residue number then insertion code with "H*" in front for hetero residues. If `full` equals `true` the chain ID is also added after a colon. Examples are "50A", "H*20" and "10:A".
