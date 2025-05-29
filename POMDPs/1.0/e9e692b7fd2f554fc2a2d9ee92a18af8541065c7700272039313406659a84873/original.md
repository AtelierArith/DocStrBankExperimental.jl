```
value(p::Policy, s)
value(p::Policy, s, a)
```

Returns the utility value from policy `p` given the state (or belief), or state-action (or belief-action) pair.

The state-action version is commonly referred to as the Q-value.
