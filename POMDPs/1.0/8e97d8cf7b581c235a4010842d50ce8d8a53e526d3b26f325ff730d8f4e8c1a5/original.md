```
actions(m::Union{MDP,POMDP})
```

Returns the entire action space of a (PO)MDP.

---

```
actions(m::Union{MDP,POMDP}, s)
```

Return the actions that can be taken from state `s`.

---

```
actions(m::POMDP, b)
```

Return the actions that can be taken from belief `b`.

To implement an observation-dependent action space, use `currentobs(b)` to get the observation associated with belief `b` within the implementation of `actions(m, b)`.
