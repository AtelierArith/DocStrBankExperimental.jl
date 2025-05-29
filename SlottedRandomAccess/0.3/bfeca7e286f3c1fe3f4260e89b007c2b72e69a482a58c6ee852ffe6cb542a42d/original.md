```
@enum ReplicaPowerStrategy SamePower IndependentPower
```

Enum used to specify how the power for replicas of a given user in a specific RA frame is determined.

# Values

  * `SamePower`: All replicas have the same power for a given user in a specific RA frame.
  * `IndependentPower`: Each replica has an independent power in each slot.
