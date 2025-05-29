```
update(msg::T, s::NMEAData) where T <: NMEAString
```

Update the last received message of type T in the NMEAData object s with the given message msg. Return the updated NMEAData object s.
