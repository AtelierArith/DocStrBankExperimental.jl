Return the full Pauli group of a given length. Phases are ignored by default, but can be included by setting `phases=true`.

```jldoctest
julia> pauligroup(1)
+ _
+ X
+ Z
+ Y

julia> pauligroup(1, phases=true)
+ _
+ X
+ Z
+ Y
- _
- X
- Z
- Y
+i_
+iX
+iZ
+iY
-i_
-iX
-iZ
-iY
```
