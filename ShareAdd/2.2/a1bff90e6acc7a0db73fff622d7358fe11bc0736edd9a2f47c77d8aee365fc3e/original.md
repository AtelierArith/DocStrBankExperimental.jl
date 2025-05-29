```
SkipAskForceEnum
```

Options for deletion of environments and packages.

  * `SKIPPING = -1`
  * `ASKING = 0`
  * `FORCING = 1`

As `ShareAdd` is intended for interactive usage, and therefore the exported bindings are available in the `Main` module, we use the "-ing" form to reduce the probability of name collisions.

The values of this enum are exported, whereas the enum type is public but not exported. 
