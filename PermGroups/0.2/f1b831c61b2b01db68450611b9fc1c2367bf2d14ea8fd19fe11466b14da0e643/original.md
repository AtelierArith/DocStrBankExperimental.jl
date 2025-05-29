`stab_onmats([G,]M;extra=nothing)`

If  `onmats(m,p)=^(M,p;dims=(1,2))`, and  the argument  `G` is given (which should   be  a  `PermGroup`)   this  is  just   a  fast  implementation  of `centralizer(G,M,onmats)`.   If  `G`   is  omitted   it  is   taken  to  be `symmetric_group(size(M,1))`.  The  program  uses sophisticated algorithms, and  can handle matrices up to 80×80. If a list `extra` is given the result centralizes also `extra`.

```julia-repl
julia> stab_onmats((1:30)'.*(1:30).%15)
Group((1,16),(4,19),(11,26),(14,29),(2,17),(7,22),(8,23),(13,28),(6,21),(9,24),(1,4)(2,8)(3,12)(6,9)(7,13)(11,14)(16,19)(17,23)(18,27)(21,24)(22,28)(26,29),(3,18),(12,27),(1,11)(2,7)(4,14)(5,10)(8,13)(16,26)(17,22)(19,29)(20,25)(23,28),(5,20),(10,25),(15,30))
```
