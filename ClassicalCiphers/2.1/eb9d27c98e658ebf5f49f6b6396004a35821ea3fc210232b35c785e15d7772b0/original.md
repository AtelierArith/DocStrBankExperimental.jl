```julia
function encrypt_enigma(plaintext,
						rotors::Array{Integer, 1}, key::AbstractString;
						reflector_id='B', ring::AbstractString = "AAA",
						stecker = Tuple{Char, Char}[],
						skip_stecker_check = false)
```

Encrypts the given plaintext according to the Enigma (M3, army version).

Arguments are in the order: `plaintext, stecker, rotors, ring, key.`

Plaintext is a string; punctuation is stripped out and it is made lowercase. Rotors is an array - for example, `[1,2,3]` - being the order of the rotors.   Each entry should be a distinct integer between 1 and 5 inclusive. Key is a string of three letters, indicating the starting positions of the rotors.

Optional:

  * `reflector_id='B'`, which sets whether to use reflector A, B or C.

Can also be specified as a 26-char string.

  * Stecker is either an array - for example,`[('A','B'), ('D', 'E')]` specifying

that A, B are swapped and D, E are swapped - or a string ("ABDE" accomplishing   the same thing). No letter may appear more than once.

  * Ring is a string - for example, "AAA" - being the offset applied to each rotor.

"AAA", for example, signifies no offset. The string must be three letters.

  * `skip_stecker_check=false`, which when `true` skips validation of stecker settings.

---

### Examples

```julia
julia> encrypt_enigma("AAA", [1,2,3], "ABC")
"CXT"

julia> encrypt_enigma("AAA", [1,2,3], "ABC", ring="AAA", reflector_id='B', stecker="") # synonymous with above
"CXT"

julia> encrypt_enigma("AAA", [1,2,3], "ABC", ring="AAA", reflector_id="YRUHQSLDPXNGOKMIEBFZCWVJAT", stecker="") # synonymous with above
"CXT"

julia> encrypt_enigma("AAA", [1,2,3], "ABC", ring="AAA", reflector_id='B', stecker=Tuple{Char, Char}[]) # synonymous with above
"CXT"
```
