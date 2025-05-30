```julia
crack_monoalphabetic(
    ciphertext;
    starting_key::AbstractString = "",
    min_temp::AbstractFloat = 0.0001,
    temp_factor::AbstractFloat = 0.97,
    acceptance_prob::AbstractFloat = ((e,ep,t) -> ep > e ? 1. : exp(-(e-ep)/t)),
    chatty::Integer = 0,
    rounds::Integer = 1
)
```

crack_monoalphabetic cracks the given ciphertext which was encrypted by the monoalphabetic substitution cipher.

Returns `(the derived key, decrypted plaintext)`.

The various optional arguments to `crack_monoalphabetic` are:

  * `starting_key=""`, which when specified (for example, as "ABCDEFGHIJKLMNOPQRSTUVWXYZ"), starts the simulation at the given key. The default causes it to start with the most common characters being decrypted to the most common English characters.
  * `min_temp=0.0001`, which is the temperature at which we stop the simulation.
  * `temp_factor=0.97`, which is the factor by which the temperature decreases each step.
  * `chatty=0`, which can be set to 1 to print whenever the key is updated, or 2 to print whenever any new key is considered.
  * `rounds=1`, which sets the number of repetitions we perform. Each round starts with the best key we've found so far.
  * `acceptance_prob=((e, ep, t) -> ep>e ? 1 : exp(-(e-ep)/t))`, which is the probability with which we accept new key of fitness ep, given that the current key has fitness e, at temperature t.

---

### Examples

```julia
julia> crack_monoalphabetic(str, chatty=0, rounds=10)
(decrypted_string, key)
```
