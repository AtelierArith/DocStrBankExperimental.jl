```
dictMeltingPoint
```

標準圧力（1atm）での元素の融点 - Wikipediaを参照

```
julia> dictMeltingPoint
Dict{Int64, Union{Nothing, Real}} with 102 entries:
  5  => 2349   
  56 => 1000   
  35 => 265.8  
  55 => 301.7  
  60 => 1297   
  30 => 692.68 
  32 => 1211.4 
  6  => nothing
  67 => 1734   
  ⋮  => ⋮
```

#### 例:

```
julia> get(dictMeltingPoint, 3, nothing)
453.65

julia> melting_point("Li")
453.65
```
