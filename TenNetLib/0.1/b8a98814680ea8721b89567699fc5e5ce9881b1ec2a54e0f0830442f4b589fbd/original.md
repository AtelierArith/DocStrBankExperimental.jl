```
const OpStrings{T} = Vector{OpString{T}}
```

Collection of `OpString`s.

#### Syntax:

```
os = OpStrings()
os += 1, "Sx" => i, "Sx" => j, "Sx" => k, ....
os += "Sx" => i, "Sx" => j, "Sx" => k, ....
```

#### Example:

```
os = OpStrings()    
for j=1:N-1
    os += 1, "Sz" => j, "Sz" => j+1
    os += 0.5, "S+" => j, "S-" => j+1
    os += 0.5, "S-" => j, "S+" => j+1
end
```
