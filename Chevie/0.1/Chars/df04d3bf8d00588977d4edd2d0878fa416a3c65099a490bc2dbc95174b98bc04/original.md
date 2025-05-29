`decompose(ct::CharTable,c::Vector;exact=true)`

decompose  class function `c` (given by its values on conjugacy classes) on irreducible  characters as  given by  `CharTable` `ct`.  By default  `c` is expected to be a virtual character so the result will be an integer vector. If  `c` is not a virtual character  give the keyword `exact=false` to get a correct result.
