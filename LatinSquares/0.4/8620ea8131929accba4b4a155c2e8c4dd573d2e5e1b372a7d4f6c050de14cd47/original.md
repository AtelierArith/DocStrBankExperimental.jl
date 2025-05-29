`A,B = ortho_latin(n)` returns a pair of orthogonal `n`-by-`n` Latin squares.

`A,B = ortho_latin(n,true)` returns a pair of orthogonal Latin squares that are transposes of each other.

`A,B = ortho_latin(n,r,s)` builds the Latin squares `latin(n,r)` and `latin(n,s)` and, if they are orthogonal, returns them as the answer. (Otherwise, throws an error.) See: `find_ortho_parameters`.
