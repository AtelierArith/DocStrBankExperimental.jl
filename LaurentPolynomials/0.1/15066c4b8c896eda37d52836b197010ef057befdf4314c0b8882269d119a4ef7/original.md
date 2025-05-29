`Pol(c::AbstractVector,v::Integer=0;check=true,copy=true)`

Make a polynomial of valuation `v` with coefficients `c`.

Then,  unless `check` is  `false` normalize the  result by making sure that `c`  has no leading or trailing zeroes (do not set `check=false` unless you are sure this is already the case).

Unless  `copy=false`  the  contents  of  `c`  are  copied (you can gain one allocation by setting `copy=false` if you know the contents can be shared)
