```
m_str(s)
```

Generate the Miller indices or Miller–Bravais indices quickly.

# Examples

```jldoctest
julia> m"[-1, 0, 1]"
3-element Miller:
 -1
  0
  1

julia> m"<2, -1, -1, 3>"
4-element MillerBravais:
  2
 -1
 -1
  3

julia> m"(-1, 0, 1)"
3-element ReciprocalMiller:
 -1
  0
  1

julia> m"(1, 0, -1, 0)"
4-element ReciprocalMillerBravais:
  1
  0
 -1
  0
```
