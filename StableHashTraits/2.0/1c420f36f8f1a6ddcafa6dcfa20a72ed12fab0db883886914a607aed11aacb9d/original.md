```
HashVersion{V}()
```

The default `hash_context` used by `stable_hash`. There are currently four versions (1-4). Version 4 should be favored when at all possible. Version 1 is the default version, so as to avoid changing the hash computed by existing code.

By explicitly passing this hash version in `stable_hash` you ensure that hash values for these fallback methods will not change even if new hash versions are developed.
